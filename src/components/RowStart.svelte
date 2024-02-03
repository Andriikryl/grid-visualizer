<script>
  import { range } from "../utils/utils";
  import CodeBox from "./CodeBox.svelte";
  import Playground from "./Playground.svelte";
  import RadioGroup from "./RadioGroup.svelte";
  let templates = [
    "1",
    "2",
    "3",
    "span 2",
    "a-start",
    "b-start",
    "c-start",
    "header-top",
    "main-top",
    "footer-top",
    "auto",
    "none",
  ];
  let currentTemplate = templates[0];
  function handleTemplateChange(event) {
    currentTemplate = event.detail;
  }
</script>

<section class="rows">
  <div class="container">
    <h3 class="rows__title">Row-start</h3>
    <div>
      <RadioGroup
        {currentTemplate}
        {templates}
        on:change={handleTemplateChange}
      />
    </div>
    <div>
      <Playground>
        <div class="parent">
          {#each range(1, 10) as item}
            <div class="child" style="--column: {currentTemplate}">
              {item}
            </div>
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
              display: grid; <br />grid-template-rows: [header-top] 1fr
              [header-bottom main-top] 1fr [main-bottom footer-top] 1fr
              [footer-bottom];
              <br /> grid-template-columns: repeat(3, 1fr); <br />
              grid-template-areas: "a a a" "b b b" "c c c";
            </p>
          </div>
          <div class="active__box">
            <span>
              .child__three <br />
            </span>
            <p class="inner__styles">
              display: grid; <br /><span class="active__line">
                grid-row-start: {currentTemplate};
              </span>
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
  .active__line {
    background-color: #1d3557;
    padding: 5px;
    color: #f1faee;
  }

  .active__box {
    margin-block-start: 10px;
    border: 1px solid #d62828;
    padding: 5px;
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
    grid-template-rows: [header-top] 1fr [header-bottom main-top] 1fr [main-bottom footer-top] 1fr [footer-bottom];
    grid-template-columns: repeat(3, 1fr);
    grid-template-areas:
      "a a a"
      "b b b"
      "c c c";
  }
  .child {
    padding: 20px;
    border: 1px solid black;
    background-color: #d62828;
    color: #ffff;
  }
  .child:nth-child(3) {
    grid-row-start: var(--column);
    background-color: #1b1b1b;
    display: flex;
    gap: 10px;
    flex-wrap: wrap;
  }
  .child:nth-child(3)::after {
    content: ".child__three{.....}";
    display: block;
  }
</style>
