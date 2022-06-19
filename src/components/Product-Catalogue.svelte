<script>
  import ProductCard from './Product-Card.svelte';
  const getLights = async () => {
    const res = await fetch('https://garnet-round-jumper.glitch.me/lights');
    
    if (res.ok) {
      const data = await res.json();
      console.log(data)
      return data
    }
  }
  
</script>
<!-- https://necessary-magnetic-bassoon.glitch.me/orders -->
<div
  class="mx-auto container px-4 md:px-6 2xl:px-0 py-12 flex justify-center items-center"
>
  <div class="flex flex-col jusitfy-start items-start">
   
    <div class="mt-3">
      <h1
        class="text-3xl lg:text-4xl tracking-tight font-semibold leading-8 lg:leading-9 text-white"
      >
        Let there be lights
      </h1>
    </div>
    
    <div
      class="mt-10 lg:mt-12 grid grid-cols-1 lg:grid-cols-3 gap-x-8 gap-y-10 lg:gap-y-0"
    >
     {#await getLights() then lights}
      {#each lights as light}
        <ProductCard {light} />
      {/each}
     {/await}
    </div>
  </div>
</div>
