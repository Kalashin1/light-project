<script>
  import { navigate } from 'svelte-navigator';
  export let text = 'button-text'
  export let route = '/shop';
</script>


<button on:click={e => navigate(`/${route}`)} class="px-10 py-3 mx-4 rounded-xl bg-black text-white font-bold shadow-lg">{ text }</button>
 