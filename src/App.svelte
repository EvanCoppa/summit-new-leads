<script>
  import Interface from "./lib/Interface.svelte";
  import LogIn from "./lib/LogIn.svelte";

  let auth = false;

  function handleChildVariableUpdate(updatedValue) {
    // This function is called when the child updates the variable
    console.log("Received update from child:", updatedValue);
    auth = updatedValue;
  }
</script>


<main class="bg-white w-[100vw]">
  <Interface />

  {#if auth}
  <Interface />
     
  {:else}
  <!-- <LogIn  bind:authStatus={auth} on:update={handleChildVariableUpdate} /> -->

  {/if}
 
  
</main>
