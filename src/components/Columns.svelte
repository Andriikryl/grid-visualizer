<script>
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
    <div class="playground">
      <div class="parent" style="grid-template-columns: {a}% {b}%">
        <div class="child">
          <p class="number">{a}</p>
        </div>
        <div class="child">
          <p class="number">{b}</p>
        </div>
      </div>
    </div>
    <div>
      <code class="cade__box">
        .parent <br />
        <p>
          <span> display: grid;</span>
          <span> grid-template-columns: {a}% {b}%;</span>
        </p>
      </code>
    </div>
  </div>
</section>

<style>
  .cade__box {
    margin-block-start: 30px;
    padding: 20px;
    border-radius: 10px;
    max-width: 350px;
    display: block;
    background-color: #fff;
  }
  .cade__box p {
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
  .playground {
    width: 100%;
    border: 1px solid black;
    padding: 20px;
    border-radius: 10px;
    background-color: #e5e5f7;
    opacity: 0.8;
    background-image: linear-gradient(#f3770a 1px, transparent 1px),
      linear-gradient(to right, #f3770a 1px, #e5e5f7 1px);
    background-size: 20px 20px;
    box-shadow:
      0 1px 1px rgba(0, 0, 0, 0.12),
      0 2px 2px rgba(0, 0, 0, 0.12),
      0 4px 4px rgba(0, 0, 0, 0.12),
      0 8px 8px rgba(0, 0, 0, 0.12),
      0 16px 16px rgba(0, 0, 0, 0.12);
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
