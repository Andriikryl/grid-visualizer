<script>
  import { range } from "../utils/utils";
  import Playground from "./Playground.svelte";
  let templates = ["1fr 1fr", "1fr 150px", "repeat(2, 2fr  1fr)", "none"];
  let currentTemplate = templates[0];
</script>

<section class="rows">
  <div class="container">
    <h3 class="rows__title">Grid-template-rows</h3>
    <div>
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
    </div>
    <Playground>
      <div class="parent" style="grid-template-columns: {currentTemplate}">
        {#each range(1, 10) as item}
          <div class="child">{item}</div>
        {/each}
      </div>
    </Playground>
  </div>
</section>

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
  .rows__title {
    color: var(--black, #1b1b1b);
    font-family: "Patrick Hand";
    font-size: 34px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    margin-block-end: 20px;
  }
  .parent {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;
  }
  .child {
    padding: 20px;
    border: 1px solid black;
    background-color: #d62828;
    color: #ffff;
  }
</style>
