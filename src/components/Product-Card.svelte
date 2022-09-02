<script>
  export let light;
  import Cart from '../stores/cart-store';

  const _addToCart = async (light) => {
    light.amount = 1;
    Cart.update(lights => {
      return [light, ...lights];
    })
  }
</script>


<div class="flex flex-col my-2 text-white">
  <div class="relative">
    <img
      loading="lazy"
      class="object-cover w-full h-80"
      src={light.url}
      alt="bag"
    />
    <button
      aria-label="close"
      class="top-4 right-4 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-800 absolute p-1.5 bg-gray-800 dark:bg-white dark:text-gray-800 text-white hover:text-gray-400"
    >
      <svg
        class="fil-current"
        width="14"
        height="14"
        viewBox="0 0 14 14"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M13 1L1 13"
          stroke="currentColor"
          stroke-width="1.25"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
        <path
          d="M1 1L13 13"
          stroke="currentColor"
          stroke-width="1.25"
          stroke-linecap="round"
          stroke-linejoin="round"
        />
      </svg>
    </button>
  </div>
  <div class="mt-6 flex justify-between items-center">
    <div class="flex justify-center items-center">
      <p
        class="tracking-tight text-2xl font-semibold leading-6 text-white"
      >
        { light.title }
      </p>
    </div>
    <div class="flex justify-center items-center">
      <button
        aria-label="show menu"
        class="focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-800 py-2.5 px-2 bg-gray-800 dark:bg-white dark:text-gray-800 text-white hover:text-gray-400 hover:bg-gray-200"
      >
        <svg
          id="chevronUp1"
          class="fill-stroke" 
          width="10"
          height="6"
          viewBox="0 0 10 6"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M9 5L5 1L1 5"
            stroke="currentColor"
            stroke-width="1.25"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
        <svg
          id="chevronDown1"
          class="hidden fill-stroke"
          width="10"
          height="6"
          viewBox="0 0 10 6"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M1 1L5 5L9 1"
            stroke="currentColor"
            stroke-width="1.25"
            stroke-linecap="round"
            stroke-linejoin="round"
          />
        </svg>
      </button>
    </div>
  </div>
  <div id="menu1" class="flex flex-col jusitfy-start items-start mt-12">
    <div class="mt-6">
      <p
        class="tracking-tight text-base font-medium leading-4 text-white"
      >
        N{light.price}
      </p>
    </div>
    <div
      class="flex jusitfy-between flex-col lg:flex-row items-center mt-10 w-full space-y-4 lg:space-y-0 lg:space-x-4 xl:space-x-8"
    >
      
      <div class="w-full">
        <button
          class="focus:outline-none focus:ring-gray-800 focus:ring-offset-2 focus:ring-2 text-white w-full tracking-tight py-4 text-lg leading-4 hover:bg-black bg-gray-800 border border-gray-800 dark:hover:bg-gray-700 dark:hover:text-white"

          on:click={e => _addToCart(light)}
          >Add to cart</button
        >
      </div>
    </div>
  </div>
</div>