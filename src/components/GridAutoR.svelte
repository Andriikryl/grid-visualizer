<script>
  import { range } from "../utils/utils";
  import CodeBox from "./CodeBox.svelte";
  import Playground from "./Playground.svelte";
  let templates = ["100px", "150px", "1fr", "none"];
  let currentTemplate = templates[0];
</script>

<section class="repeat">
  <div class="container">
    <h3 class="rows__title">grid-auto-rows - function</h3>
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
    <div>
      <Playground>
        <div class="parent" style="grid-auto-rows: {currentTemplate};">
          {#each range(1, 4) as item}
            <div class="child">{item}</div>
          {/each}
        </div>
      </Playground>
      <div>
        <CodeBox>
          <div>
            <span>
              .parent <br />
            </span>
            <p class="inner__styles">
              display: grid; <br />
              grid-template-rows: 50px; <br />
              gap: 20px; <br />
              grid-auto-rows: {currentTemplate};
            </p>
          </div>
        </CodeBox>
      </div>
    </div>
  </div>
</section>

<style>
  .repeat {
    margin-block-end: 20px;
  }
  .inner__styles {
    margin-inline-start: 20px;
  }
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
    grid-template-rows: 50px;
    gap: 20px;
  }
  .child {
    padding: 20px;
    border: 1px solid black;
    background-color: #d62828;
    color: #ffff;
  }
</style>
