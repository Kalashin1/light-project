<script>
  import { createEventDispatcher } from "svelte";

  let lightTypes = ["Lamp", "Bulb", "Chandelier", undefined];

  const dispatch = createEventDispatcher();

  function changeLightType(type) {
    dispatch("changeLightType", {
      type,
    });
  }
</script>

<div class="mb-4">
  <div class="px-4 sm:px-8 max-w-5xl m-auto">
    <h1 class="text-center font-semibold text-xl">Select Light Type</h1>
    <p class="mt-2 text-center text-xs mb-4 text-gray-500">
      Select between the type of light you want
    </p>
    <ul class="border border-gray-200 rounded overflow-hidden shadow-md">
      {#each lightTypes as lightType}
        {#if lightType}
          <li
            class="px-4 py-2 cursor-pointer hover:bg-sky-100 hover:text-sky-900 border-b last:border-none border-gray-200 transition-all duration-300 ease-in-out"
            on:click={(e) => changeLightType(lightType.toLowerCase())}
          >
            {lightType}
          </li>
        {/if}
      {/each}
    </ul>
    <!-- <a
      href="mailto:jefte_caro@yahoo.com"
      class="text-xs text-center block mt-4 hover:underline">@me</a
    > -->
  </div>
</div>
