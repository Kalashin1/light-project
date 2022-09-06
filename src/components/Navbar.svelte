<script>
  export let links;
  import { Link } from 'svelte-navigator';
  $:showNav = true;

  function updateShowNav(){
    showNav = !showNav;
    console.log(showNav)
  }

</script>

<nav class="sm:flex justify-between px-4 md:py-8 z-20 relative bg-transparent">
  <div class="flex justify-between py-4">
    <Link to="/" class="bg-transparent relative -top-4 md:-top-8 border-0 text-gray-50 font-bold text-xl">
      <img src='/logo-new.png' alt="Helvic Gleam" class="h-16 w-24 md:h-16 md:w-14 object-fit" />
    </Link>

    <span class="sm:hidden" on:click={e => updateShowNav()}>
      <i class="fas fa-bars cursor-pointer"></i>
    </span>
  </div>


  <ul class="sm:flex">
    {#if showNav}  
      {#each links as link}
        <li class="my-4"><Link to={`/${link.link}`} class="hover:no-underline">
          <span class="px-2 md:px-8 capitalize py-6 md:py-6 bg-transparent border-0 text-white font-bold text-xl">
            { link.text }
          </span></Link></li>
      {/each}
    {/if}
  </ul>
</nav>