<script>
  import { range } from "../utils/utils";
  import CodeBox from "./CodeBox.svelte";
  import Playground from "./Playground.svelte";
  import RadioGroup from "./RadioGroup.svelte";
  let templates = ["1fr 1fr", "1fr 150px", "repeat(2, 2fr  1fr)", "none"];
  let currentTemplate = templates[0];
  function handleTemplateChange(event) {
    currentTemplate = event.detail;
  }
</script>

<section class="rows">
  <div class="container">
    <h3 class="rows__title">Grid-template-rows</h3>
    <div>
      <RadioGroup
        {currentTemplate}
        {templates}
        on:change={handleTemplateChange}
      />
    </div>
    <div>
      <Playground>
        <div class="parent" style="grid-template-columns: {currentTemplate}">
          {#each range(1, 10) as item}
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
              display: grid; <br /> grid-template-columns: repeat(3, 1fr);
              <br /> grid-template-rows: {currentTemplate};
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
