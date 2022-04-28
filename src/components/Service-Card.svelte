<script>
  export let title;
  export let text;
  export let src;
</script>

<div class="bg-gray-800 rounded-2xl shadow-xl px-8 py-12 sm:px-12 lg:px-8">
  <div class="mb-12 space-y-4">
      <h3 class="text-2xl font-semibold text-gray-300">{ title }</h3>
      <p class="text-gray-300">{ text }</p>
      <a href="#!" class="block font-medium text-gray-300">Know more</a>
  </div>
  <img src={src} class="w-2/3 ml-auto -mb-12" alt="illustration" loading="lazy" width="900" height="600">
</div>