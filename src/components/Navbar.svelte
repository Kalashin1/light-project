<script>
  export let links;
  import { Link, link } from 'svelte-navigator';
  import { children } from 'svelte/internal';
  $:showNav = true;

  function updateShowNav(){
    showNav = !showNav;
    console.log(showNav)
  }

</script>

<nav class="sm:flex justify-between px-4 md:py-8 z-20 relative bg-transparent">
  <div class="flex justify-between py-4">
    <Link to="/" class="bg-transparent relative -top-4 md:-top-8 border-0 text-gray-50 font-bold text-xl">
      <img src='/logo-new.png' alt="Helvic Gleams" class="h-16 w-24 md:h-16 md:w-14 object-fit" />
    </Link>

    <span class="sm:hidden" on:click={e => updateShowNav()}>
      <i class="fas fa-bars cursor-pointer"></i>
    </span>
  </div>


  <ul class="md:flex md:bg-transparent" style="background-color: rgba(0, 0, 0, 0.5);">
    {#if showNav}  
      {#each links as link}
        <li class="mt-4 mb">
          <Link to={`/${link.link}`} class="hover:no-underline">
            <span class="px-2 flex flex-col md:px-2 capitalize py-2 md:py-4 bg-transparent border-0 text-white font-bold text-md">
              { link.text }
            </span>
          </Link>
          {#if link.children}
            {#each link.children as childLink }
              <li class="my">
                <Link to={`/${childLink.link}`}>
                  <span class="px-2 md:px-2 capitalize py-2 md:py-4 bg-transparent border-0 text-white font-bold text-sm">
                    {childLink.text}
                  </span>
                </Link>
              </li>
            {/each}
          {/if}
        </li>
      {/each}
    {/if}
  </ul>
</nav>