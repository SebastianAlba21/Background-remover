<script lang="ts">
  import { Cloudinary } from "@cloudinary/url-gen";
  import { backgroundRemoval } from "@cloudinary/url-gen/actions/effect";
  import { ImageStatus } from "../types.d";
  import { imageStatus, modifiedImage, originalImage } from "./store";
  import Dropzone from "dropzone";
  import "dropzone/dist/dropzone.css";
  import { onMount } from "svelte";

  const cloudinary = new Cloudinary({
    cloud: {
      cloudName: "dbhsidcc0",
    },
    url: {
      secure: true,
    },
  });

  onMount(() => {
    const dropzone = new Dropzone("#dropzone", {
      uploadMultiple: false,
      acceptedFiles: ".webp,.jpg,.png,.jpeg",
      maxFiles: 1,
    });
    dropzone.on("sending", (file, xhr, formData) => {
      formData.append("upload_preset", "Sebastian");
      formData.append("timestamp", Date.now());
      formData.append("api_key", 233415771816374);
    });
    dropzone.on("success", (file, response) => {
      const { public_id: publicId, secure_url: url } = response;
      /* 
      Crear la imagen con fondo transparente
      y guardarla en la carpeta de Cloudinary
      */
      const imageWithoutBackground = cloudinary
        .image(publicId)
        .effect(backgroundRemoval());
      imageStatus.set(ImageStatus.DONE);
      modifiedImage.set(imageWithoutBackground.toURL());
      originalImage.set(url);
      console.log(modifiedImage);
    });
    dropzone.on("error", (file, response) => {
      console.log(response);
    });
  });
</script>

<form
  id="dropzone"
  class="shadow-2xl border-dashed border-2 border-gray-300 rounded-lg aspect-video w-full flex items-center justify-center flex-col"
  action="https://api.cloudinary.com/v1_1/dbhsidcc0/image/upload"
>
  {#if $imageStatus === ImageStatus.READY}
    <button
      class="font-bold bg-green-600 rounded-full text-white px-6 py-4 hover:bg-green-900"
    >
      Upload files here
    </button>
    <strong class="text-lg mt-4 text-gray-800">Or drop your file</strong>
  {/if}

  {#if $imageStatus === ImageStatus.UPLOADING}
    <strong class="text-lg mt-4 text-gray-800">Uploading files..</strong>
  {/if}
</form>
