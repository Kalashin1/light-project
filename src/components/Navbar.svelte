<script>
  export const links = ["Home", "Lights", "About", "Contact"]
</script>

<nav class="md:flex justify-between md:py-6 z-20 relative">
  <div>
    <a href="#!" class="px-4 py-2 text-gray-50 font-bold text-xl">Logo</a>

    <button class="md:hidden">menu</button>
  </div>


  <ul class="md:flex">
    {#each links as link}
      <li><a href="#!" class="px-8 py-6 text-white font-bold text-xl">{ link }</a></li>
    {/each}
  </ul>
</nav>