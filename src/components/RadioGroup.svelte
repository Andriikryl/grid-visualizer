<script>
  let currentTemplate;
  let templates;
</script>

<form class="form">
  {#each templates as template}
    <label>
      <input
        type="radio"
        name="flavours"
        value={template}
        bind:group={currentTemplate}
      />
      {template}
    </label>
  {/each}
</form>

<style>
  .form {
    display: flex;
    flex-direction: column;
    gap: 10px;
    margin-block-end: 20px;
    background-color: #fefae0;
    padding: 20px;
    border-radius: 10px;
    max-width: 300px;
  }
</style>
