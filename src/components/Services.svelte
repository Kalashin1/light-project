<script>
  import { services } from '../services';
  import ServiceCard from './Service-Card.svelte';
</script>

<!-- component -->
<section class="py-8 bg-black relative top-8">  
  <h1 class="mb-8 font-bold text-white text-center text-3xl my-10">Services</h1>
  <div class="container m-auto px-6 text-gray-500 md:px-12 xl:px-0">
      <div class="mx-auto grid gap-6 md:w-3/4 lg:w-full lg:grid-cols-3">
          {#each services as service }
            <ServiceCard bind:src={service.src} bind:text={service.text} bind:title={service.title} />
          {/each}
      </div>
  </div>
</section>