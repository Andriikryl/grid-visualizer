<script>
  import { range } from "../utils/utils";
  import CodeBox from "./CodeBox.svelte";
  import Playground from "./Playground.svelte";
  let templates = [
    "100px 40%",
    "10% 30% 50% 10%",
    "1fr 3fr;",
    "1fr auto",
    "repeat(7, 1fr)",
    "repeat(3, 1fr auto)",
    "1fr minmax(min-content, 3fr)",
    "2fr max-content",
    "min-content min-content",
    "max-content max-content",
    "fit-content(10%) fit-content(50%)",
  ];
  let currentTemplate = templates[0];
</script>

<section class="list">
  <div class="container">
    <h3 class="list__title">List-template-rows</h3>
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
    <div class="box">
      <Playground>
        <div class="parent" style="grid-template-columns: {currentTemplate}">
          {#each range(1, 7) as item}
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
  .list {
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
  .list__title {
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
