<script></script>

<code class="cade__box">
  <slot />
</code>

<style>
  .cade__box {
    margin-block-start: 30px;
    padding: 20px;
    border-radius: 10px;
    max-width: 350px;
    display: block;
    background-color: #fff;
    position: relative;
  }
  .cade__box::after {
    content: "";
    background-image: url("/arrows/Arrow-curved.svg");
    background-size: cover;
    background-repeat: no-repeat;
    display: block;
    width: 50px;
    height: 50px;
    position: absolute;
    top: -30px;
    right: -50px;
    transform: matrix(-1, 0, 0, 1, 0, 0);
  }
</style>
