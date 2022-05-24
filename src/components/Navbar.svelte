<script>
  export let links;
  import { Link } from 'svelte-navigator';
  $:showNav = true;

  function updateShowNav(){
    showNav = !showNav;
    console.log(showNav)
  }

</script>

<nav class="sm:flex justify-between md:py-6 z-20 relative">
  <div class="flex justify-between">
    <button href="#!" class="px-4 py-2 bg-transparent border-0 text-gray-50 font-bold text-xl">Logo</button>

    <button class="sm:hidden px-4" on:click={e => updateShowNav()}>
      <i class="fas fa-bars cursor-pointer"></i>
    </button>
  </div>


  <ul class="sm:flex">
    {#if showNav}  
      {#each links as link}
        <li><Link to={`/${link.link}`} class="hover:no-underline">
          <span class="px-8 capitalize py-6 bg-transparent border-0 text-white font-bold text-xl">
            { link.text }
          </span></Link></li>
      {/each}
    {/if}
  </ul>
</nav>