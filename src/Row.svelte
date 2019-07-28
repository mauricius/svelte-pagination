<script>
  export let row;

  import Modal from './Modal.svelte';

  let showModal = false;

  $: fullname = `${row.name} ${row.surname}`;
</script>

<tr>
  <td>{row.id}</td>
  <td>{row.name}</td>
  <td>{row.surname}</td>
  <td>
    <button on:click="{() => showModal = true}">
      Details
    </button>
  </td>
</tr>

{#if showModal}
<Modal on:close="{() => showModal = false}">
  <h4 class="title" slot="header">
    Details for User <code>{row.id}</code>
  </h4>

  <p><code>{fullname} ({row.email})</code></p>
  <p>Current mood: {row.mood}</p>
</Modal>
{/if}

<style>
  tr td {
    text-align: center;
  }

  .title {
    margin: 0;
  }
</style>