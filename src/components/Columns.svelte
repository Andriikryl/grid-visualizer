<script>
  import CodeBox from "./CodeBox.svelte";
  import Playground from "./Playground.svelte";

  let a = 30;
  let b = 70;
  $: {
    if (a > 100) {
      a = 100;
      b = 0;
    } else {
      b = 100 - a;
    }
  }

  $: {
    if (b > 100) {
      b = 100;
      a = 0;
    } else {
      a = 100 - b;
    }
  }
</script>

<section class="columns">
  <div class="container">
    <h3 class="colums__title">Grid-template-columns</h3>
    <div class="controls">
      <label>
        <input type="number" bind:value={a} min="1" max="99" />
        <input type="range" bind:value={a} min="1" max="99" />
      </label>
      <label>
        <input type="number" bind:value={b} min="1" max="99" />
        <input type="range" bind:value={b} min="1" max="99" />
      </label>
    </div>
    <Playground>
      <div class="parent" style="grid-template-columns: {a}% {b}%">
        <div class="child">
          <p class="number">{a}</p>
        </div>
        <div class="child">
          <p class="number">{b}</p>
        </div>
      </div>
    </Playground>
    <div>
      <CodeBox>
        .parent <br />
        <p class="code">
          <span> display: grid;</span>
          <span> grid-template-columns: {a}% {b}%;</span>
        </p>
      </CodeBox>
    </div>
  </div>
</section>

<style>
  .code {
    display: flex;
    flex-direction: column;
    margin-inline-start: 20px;
  }
  .columns {
    margin-block-end: 30px;
  }
  .colums__title {
    color: var(--black, #1b1b1b);
    font-family: "Patrick Hand";
    font-size: 34px;
    font-style: normal;
    font-weight: 400;
    line-height: normal;
    margin-block-end: 20px;
  }
  .controls {
    margin-block-end: 20px;
  }
  .parent {
    display: grid;
    overflow: hidden;
    gap: 10px;
  }
  .child {
    border: 3px dashed #e63946;
    padding: 20px;
    background-color: #14213d;
    display: grid;
    place-items: center;
  }
  .number {
    color: var(--white, #fff);
    text-align: center;
    font-family: "Patrick Hand";
    font-size: 22px;
    font-style: normal;
    font-weight: 400;
    line-height: 28px;
  }
</style>
