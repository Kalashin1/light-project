<script>
  let show = true;
  import { navigate } from "svelte-navigator";
  import { onDestroy } from "svelte";
  import Cart from "../stores/cart-store";
  import { db } from "../firebase-settings";
  import PaymentComponent from "./PaymentComponent.svelte";
  import {
    collection,
    addDoc,
    getDocs,
    doc,
    where,
    query,
  } from "firebase/firestore";
  let lights = [];

  const unsubscribeFromStore = Cart.subscribe((cart) => (lights = cart));

  onDestroy(() => unsubscribeFromStore());

  function hidePayment (){
    showPayment = false;
    navigate("/order-placed");
  }

  $:showPayment = false;
  let url;

  let user = {
    fullName: "",
    phone: "",
    deliveryAddress: "",
  };

  let createUser = async (name, phone) => {
    const docRef = await addDoc(collection(db, "users"), {
      name,
      phone,
    });
  };

  let getUser = async (phone) => {
    const q = query(collection(db, "users"), where("phone", "==", phone));
    const querySnapshot = await getDocs(q);
    if (querySnapshot.docs.length) {
      console.log(querySnapshot);
      const user = querySnapshot.docs[0].data();
      user.id = querySnapshot.docs[0].id;
      return user;
    } else {
      return false;
    }
  };

  let makeOrder = async (lights, user, deliveryLocation) => {
    const lightsTotal = lights.map(l => parseInt(l.amount) * parseInt(l.price));
    const total = lightsTotal.reduce((prev, next) => prev + next);
    console.log(total)
    const res = await fetch('https://caterwauling-moored-griffin.glitch.me/transaction', {
      headers: { "Content-Type": "application/json"},
      body: JSON.stringify({ email: 'payment@gmail.com', amount: total }),
      method: 'post'
    })
    if (res.ok) {
      const { data } = await res.json();
      console.log(data.data.authorization_url);
      url = data.data.authorization_url
      showPayment = true
      await await addDoc(collection(db, "orders"), {
        lights,
        reference: data.data.reference,
        user,
        deliveryLocation,
        status: "pending",
        createdAt: new Date().getTime(),
        affiliate: localStorage.getItem('affilate')
      });
    }
    
  };

  let createAccount = async () => {
    console.log(user.fullName);
    let existedUser = await getUser(user.phone);

    if (existedUser) {
      
      await makeOrder(
        lights,
        { name: user.fullName, phone: user.phone },
        user.deliveryAddress
      );
      
    } else {
      await createUser(user.fullName, user.phone);
      await makeOrder(
        lights,
        { name: user.fullName, phone: user.phone },
        user.deliveryAddress
      );
    }
  };
</script>

<!-- component -->
<svelte:head>
  <script
    defer
    src="https://cdn.jsdelivr.net/gh/alpinejs/alpine@v2.x.x/dist/alpine.js"></script>
</svelte:head>


<div class="container max-w-full h-screen mx-auto bg-gray-900 py-24 px-6 relative">
  {#if showPayment}
    <PaymentComponent url={url} on:click={hidePayment} />
  {/if}
  <div class="font-sans">
    <div class="max-w-sm mx-auto px-6">
      <div class="relative flex flex-wrap">
        <div class="w-full relative">
          <div class="mt-6">
            <div
              class="mb-5 pb-1border-b-2 text-center font-base text-gray-700"
            />
            <div class="text-center font-semibold text-gray-50">
              Please enter your Details to proceed?
            </div>

            <form
              class="mt-8"
              on:submit|preventDefault={(e) => createAccount()}
            >
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
                  <span class="px-1 text-sm text-gray-600"
                    >Delivery Address</span
                  >
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
