<script>
  import { navigate } from 'svelte-navigator'
  import { createEventDispatcher } from 'svelte';

  export let cart;
  console.log(cart);

  const dispatch = createEventDispatcher();

  let totalArr, total;

  if (cart.length > 0) {
    totalArr = cart.map((item) => item.amount * item.price);
    total = totalArr.reduce((prev, next) => prev + next);
  }

  function editAmount(amount, id) {
		dispatch('editAmount', {
			amount,
      id
		});
	}
  
</script>

<div class="bg-gray-900 h-full md:h-screen text-gray-900">
  <div class="grid grid-cols-12 gap-6">
    <div
      class="col-span-12 sm:col-span-12 md:col-span-7 lg:col-span-8 xxl:col-span-8"
    >
      <div class="bg-white py-4 px-4 shadow-xl rounded-lg my-4 mx-4 border-b-2 mb-2">
        {#if cart.length}
          {#each cart as cartItem}
            <div class="flex justify-between px-4 items-center">
              <div class="text-lg font-semibold">
                <p>{cartItem.title}</p>
                <p class="text-gray-400 text-base">$ {cartItem.price}</p>
              </div>
              <div>
                <!-- <img /> -->
              </div>
              <div class="text-lg font-semibold">
                <button
                  class="focus:outline-none bg-pink-700 hover:bg-pink-800 text-white font-bold py-2 px-2 rounded-full inline-flex items-center "
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-6 w-6"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                  >
                    <path
                      stroke-linecap="round"
                      stroke-linejoin="round"
                      stroke-width="2"
                      d="M12 9v3m0 0v3m0-3h3m-3 0H9m12 0a9 9 0 11-18 0 9 9 0 0118 0z"
                    />
                  </svg>
                </button>
              </div>
            </div>
          {/each}
        {/if}

        {#if !cart.length}
        <div class="flex justify-between px-4 items-center">
          <div class="text-lg font-semibold">
            <p>There are no items in your cart yet</p>
            <p class="text-gray-400 text-base">$ 0.00</p>
          </div>
          
        </div>
        {/if}
        
      </div>
      {#if cart.length}  
        <div class="bg-pink-700 cursor-pointer text-white py-4 px-4 shadow-xl rounded-lg my-4 mx-4"
        on:click={e => navigate('/details')}
        >
          <!-- Checkout Button -->
          <div class="flex justify-center items-center text-center">
            <div class="text-xl font-semibold">
              <p>Place Order</p>
              <p class="text-5xl">${total}</p>
            </div>
          </div>
          <!-- End Checkout Button -->
        </div>
      {/if}
    </div>
    <div
      class="col-span-12 sm:col-span-12 md:col-span-5 lg:col-span-4 xxl:col-span-4"
    >
      <div class="bg-white py-4 px-4 shadow-xl rounded-lg my-4 mx-4">
        {#if cart.length > 0}
          {#each cart as cartItem}
            <!-- classic add -->
            <div class="flex justify-between border-b-2 mb-2">
              <div class="text-lg py-2">
                <p>{cartItem.title}</p>
              </div>
              <div class="text-lg py-2">
                <div
                  class="flex flex-row space-x-2 w-full items-center rounded-lg"
                >
                  <button
                    class="focus:outline-none bg-pink-700 hover:bg-pink-800 text-white font-bold py-1 px-1 rounded-full inline-flex items-center"
                    on:click={e => editAmount(-1, cartItem.id)}
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-4 w-4"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M18 12H6"
                      />
                    </svg>
                  </button>
                  <p>{cartItem.amount}</p>
                  <button
                    class="focus:outline-none bg-pink-700 hover:bg-pink-800 text-white font-bold py-1 px-1 rounded-full inline-flex items-center"
                    on:click={e => editAmount(+1, cartItem.id)}
                  >
                    <svg
                      xmlns="http://www.w3.org/2000/svg"
                      class="h-4 w-4"
                      fill="none"
                      viewBox="0 0 24 24"
                      stroke="currentColor"
                    >
                      <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M12 6v6m0 0v6m0-6h6m-6 0H6"
                      />
                    </svg>
                  </button>
                </div>
              </div>
            </div>
            <!-- End classic add -->
          {/each}
        {/if}

        <!-- Total Item -->
        <div class="flex justify-center items-center text-center">
          <div class="text-xl font-semibold">
            <p>Total Item</p>
            <p class="text-5xl">{cart.length}</p>
          </div>
        </div>
        <!-- End Total Item -->
      </div>
      <div class="bg-white py-4 px-4 shadow-xl rounded-lg my-4 mx-4">
        <!-- Total Price -->
        <div class="flex justify-center items-center text-center">
          <div class="text-xl font-semibold">
            <p>Total Price</p>
            {#if total}
              
              <p class="text-5xl">${total}</p>
            {/if}
          </div>
        </div>
        <!-- End Total PRice -->
      </div>
    </div>
  </div>
</div>
