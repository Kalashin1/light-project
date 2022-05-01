<script>
  export const links = ["Home", "shop", "About", "Contact"]
  import { Link } from 'svelte-navigator';
</script>

<nav class="md:flex justify-between md:py-6 z-20 relative">
  <div>
    <button href="#!" class="px-4 py-2 bg-transparent border-0 text-gray-50 font-bold text-xl">Logo</button>

    <button class="md:hidden">menu</button>
  </div>


  <ul class="md:flex">
    {#each links as link}
      <li><Link to={link} class="px-8 capitalize py-6 bg-transparent border-0 text-white font-bold text-xl">{ link }</Link></li>
    {/each}
  </ul>
</nav>