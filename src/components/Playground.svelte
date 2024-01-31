<script></script>

<div class="wrapper">
  <div class="playground">
    <slot />
  </div>
  <div class="playground__description">
    <div>
      <img width="100" height="100" src="/arrows/Arrow-curved.svg" alt="" />
    </div>
    <div class="desciprion__text">
      <p>.parent</p>
    </div>
  </div>
</div>

<style>
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
  .playground__description {
    margin-block-start: 20px;
    width: max-content;
    display: flex;
    align-items: center;
    gap: 20px;
    margin-inline-start: auto;
  }
  .desciprion__text {
    background-color: #fff;
    border-radius: 10px;
    padding: 30px;
    border: 2px solid #ffb703;
  }
</style>
