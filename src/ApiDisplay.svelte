<script>
  import { onMount } from 'svelte';

  let items = [];
  let loading = true;
  let error = null;

  onMount(async () => {
    try {
      const res = await fetch('/api/items'); // <-- fetch /items through proxy
      if (!res.ok) throw new Error('Failed to fetch API');

      items = await res.json();
    } catch (e) {
      error = e.message;
    } finally {
      loading = false;
    }
  });
</script>
{#if loading}
  <p>Loading...</p>
{:else if error}
  <p style="color: red;">Error: {error}</p>
{:else}
  <ul>
    {#each items as item}
      <li>{JSON.stringify(item)}</li>
    {/each}
  </ul>
{/if}
