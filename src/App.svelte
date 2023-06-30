<script lang="ts">
  import CloudinaryLogo from "./CloudinaryLogo.svelte";
  import SvelteLogo from "./SvelteLogo.svelte";
  import TypescriptLogo from "./TypescriptLogo.svelte";
  import StepUpload from "./StepUpload.svelte";
  import StepEdit from "./StepEdit.svelte";
  import { imageStatus } from "./store";
  import { ImageStatus } from "../types.d";
</script>

<div class="m-auto max-w-2xl flex flex-col justify-between w-full h-screen">
  <header class="flex flex-col justify-center items-center mt-10 pt-5">
    <h1 class="text-3xl font-bold text-green-900 tracking-tighter">
      RemoveUr<span class="text-green-600">Background</span>
    </h1>
  </header>

  <main class="w-full block">
    {#if $imageStatus === ImageStatus.READY || $imageStatus === ImageStatus.UPLOADING}
      <StepUpload />
    {:else if $imageStatus === ImageStatus.DONE}
      <StepEdit />
    {/if}
  </main>

  <footer
    class="flex justify-center items-center gap-x-2 font-semibold text-xl py-2 "
  >
    Made with <a
      class="pb-2"
      href="https://cloudinary"
      target="_blank"
      rel="noreferrer"
    >
      <CloudinaryLogo /></a
    >
  </footer>
  <h1
    class="flex justify-center items-center gap-x-2 font-bold italic text-sm py-2 text-neutral-300"
  >
    This app was build with <SvelteLogo />
    <TypescriptLogo />
  </h1>
</div>
