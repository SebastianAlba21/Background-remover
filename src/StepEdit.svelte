<script lang="ts">
  import "two-up-element";
  import { originalImage, modifiedImage } from "./store";

  let proccesingImage = true;
  let tries = 0;
  let intervalId: any;
  $: {
    if (proccesingImage) {
      clearInterval(intervalId);
      intervalId = setInterval(() => {
        tries++;
        const img = new Image();
        img.src = $modifiedImage;
        img.onload = () => {
          proccesingImage = false;
          clearInterval(intervalId);
        };
      }, 500);
    }
  }
</script>

<two-up>
  <!-- svelte-ignore a11y-img-redundant-alt -->
  <img src={$originalImage} alt="Original Image" />
  {#if proccesingImage}
    <div class="flex flex-col items-center justify-center">
      <div
        class="loader ease-linear rounded-full border-4 border-t-4 border-gray-200 h-12 w-12 mb-4"
      />
      <h2 class="text-xl font-semibold">Processing your image</h2>
      <p class="text-gray-500">This may take a few seconds</p>
    </div>
  {:else}
    <!-- svelte-ignore a11y-img-redundant-alt -->
    <img src={$modifiedImage} alt="Image without background" />
  {/if}
</two-up>

<a
  download
  href={$modifiedImage}
  class="block bg-green-500 hover:bg-green-700 text-center text-xl w-full font-bold text-white rounded-full px-4 py-2 mt-4"
>
  Download your image without background
</a>
