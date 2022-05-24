<script>
  import { navigate } from 'svelte-navigator'
</script>

<!-- component -->
<div class="w-full">
  <div class="grid grid-cols-1 md:grid-cols-2 h-screen">
    <div class="max-h-96 md:h-screen">
      <img class="w-screen h-screen object-cover object-top" src="/images/vintage-ceiling-light-lamp-min.jpg" alt="">
    </div>
    <div class="flex bg-black p-10 text-white">
      <div class="mb-auto mt-auto max-w-lg">
        <h1 class="text-3xl uppercase my-6">Light Company</h1>
        <p class="font-semibold mb-5 my-4">Indoor Decor</p>
        <p>We have an existing array of breath-taking lighting for your living rooms, bedroom, kitchen and just about any place that needs lighting. </p>
        <button class="bg-gray-800 rounded-md py-3 px-7 mt-6 text-white" on:click={e => navigate('/shop')}>Check Out Our Store</button>
      </div>
    </div>
  </div>
</div>