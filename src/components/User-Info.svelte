<script>
  let show = true;
  import { navigate } from "svelte-navigator";
  import { onDestroy } from "svelte";
  import Cart from '../stores/cart-store'
  let lights = []

  const unsubscribeFromStore = Cart.subscribe(cart => lights = cart);

  onDestroy(() => unsubscribeFromStore())

  let user = {
    fullName: "",
    phone: "",
    deliveryAddress: ''
  };

  let createUser = async (fullName, phone) => {
    const res = await fetch("http://localhost:3000/users", {
      method: "POST",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({ fullName, phone }),
    });

    if (res.ok) {
      const user = await res.json();
      return user;
    } else {
      return false;
    }
  };

  let makeOrder = async (lights, user, deliveryLocation) => {
    const res = await fetch('http://localhost:3000/orders', {
      method: 'post',
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify({
        lights,
        user,
        deliveryLocation
      })
    });

    if (res.ok) {
      const data = await res.json()
      return data;
    } else {
      console.log(`error ${await res.json()}`)
    }
  }

  let createAccount = async () => {
    console.log(user.fullName);
    let doesUserExistRes = await fetch(
      `http://localhost:3000/users/phone/${user.phone}`
    );

    if (doesUserExistRes.ok) {
      const data = await doesUserExistRes.json();

      if (data._id) {
        console.log(data);
        const order = await makeOrder(lights, data._id, user.deliveryAddress)
        navigate('/order-placed')
      } else {
        const RegUser = await createUser(user.fullName, user.phone);
        console.log(RegUser._id);
        const order = await makeOrder(lights, RegUser._id, user.deliveryAddress);
        navigate('/order-placed')
      }
    } else{
      console.log(`error ${await res.json()}`);
    }
  };
</script>

<!-- component -->
<svelte:head>
  <script
    defer
    src="https://cdn.jsdelivr.net/gh/alpinejs/alpine@v2.x.x/dist/alpine.js"></script>
</svelte:head>

<div class="container max-w-full h-screen mx-auto bg-gray-900 py-24 px-6">
  <div class="font-sans">
    <div class="max-w-sm mx-auto px-6">
      <div class="relative flex flex-wrap">
        <div class="w-full relative">
          <div class="mt-6">
            <div
              class="mb-5 pb-1border-b-2 text-center font-base text-gray-700"
            >
            </div>
            <div class="text-center font-semibold text-gray-50">
              Please enter your Details to proceed?
            </div>

            <form class="mt-8" on:submit|preventDefault={(e) => createAccount()}>
              <div class="mx-auto max-w-lg">
                <div class="py-2">
                  <span class="px-1 text-sm text-gray-600">Name</span>
                  <input
                    placeholder=""
                    required
                    type="text"
                    bind:value={user.fullName}
                    class="text-md block px-3 py-2  rounded-lg w-full 
                bg-white border-2 border-gray-300 placeholder-gray-600 shadow-md focus:placeholder-gray-500 focus:bg-white focus:border-gray-600 focus:outline-none"
                  />
                </div>
                <div class="py-2">
                  <span class="px-1 text-sm text-gray-600">Phone Number</span>
                  <div class="relative">
                    <input
                      placeholder=""
                      type="text"
                      required
                      bind:value={user.phone}
                      class="text-md block px-3 py-2 rounded-lg w-full 
                bg-white border-2 border-gray-300 placeholder-gray-600 shadow-md
                focus:placeholder-gray-500
                focus:bg-white 
                focus:border-gray-600  
                focus:outline-none"
                    />
                  </div>
                </div>
                <div class="py-2">
                  <span class="px-1 text-sm text-gray-600">Delivery Address</span>
                  <input
                    placeholder=""
                    type="text"
                    required
                    bind:value={user.deliveryAddress}
                    class="text-md block px-3 py-2  rounded-lg w-full 
                bg-white border-2 border-gray-300 placeholder-gray-600 shadow-md focus:placeholder-gray-500 focus:bg-white focus:border-gray-600 focus:outline-none"
                  />
                </div>
                <button
                  type="submit"
                  class="mt-3 text-lg font-semibold 
                bg-gray-800 w-full text-white rounded-lg
                px-6 py-3 block shadow-xl hover:text-white hover:bg-black"
                >
                  Place Order
                </button>
              </div>
            </form>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
