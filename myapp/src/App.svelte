<script>
  import Login from './Login.svelte';
  import Register from './Register.svelte';

  let showRegister = false;
</script>

{#if showRegister}
  <Register login={() => showRegister = false} />
{:else}
  <Login register={() => showRegister = true} />
{/if}
