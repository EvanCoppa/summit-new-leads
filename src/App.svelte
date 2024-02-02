<script>
  import Interface from "./lib/Interface.svelte";
  import LogIn from "./lib/LogIn.svelte";

  let auth = false;


</script>


<main class="bg-white w-[100vw]">
  <Interface />

  {#if auth}
  <Interface />
     
  {:else}
  <!-- <LogIn /> -->

  {/if}
 
  
</main>
