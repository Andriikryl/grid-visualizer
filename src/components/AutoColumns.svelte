<script>
  import { range } from "../utils/utils";
  import CodeBox from "./CodeBox.svelte";
  import Playground from "./Playground.svelte";
  import RadioGroup from "./RadioGroup.svelte";
  let templates = ["75px", "150px", "1fr", "none"];
  let currentTemplate = templates[0];
  function handleTemplateChange(event) {
    currentTemplate = event.detail;
  }
</script>

<section class="rows">
  <div class="container">
    <h3 class="rows__title">Grid-auto-columns</h3>
    <div>
      <RadioGroup
        {currentTemplate}
        {templates}
        on:change={handleTemplateChange}
      />
    </div>
    <div>
      <Playground>
        <div class="parent" style="grid-auto-columns: {currentTemplate}">
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
              display: grid; <br /> grid-template-columns: 50px;
              <br /> grid-auto-columns: {currentTemplate}; <br />
              grid-auto-flow: column;
            </p>
          </div>
        </CodeBox>
      </div>
    </div>
  </div>
</section>

<style>
  .rows {
    margin-block-end: 20px;
  }
  .inner__styles {
    margin-inline-start: 20px;
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
    grid-template-columns: 50px;
    grid-auto-columns: 75px;
    grid-auto-flow: column;
  }
  .child {
    padding: 20px;
    border: 1px solid black;
    background-color: #d62828;
    color: #ffff;
  }
</style>
