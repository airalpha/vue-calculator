<template>
  <div class="calculator">
    <h1 class="title">Vue Calculator</h1>
    <div class="display">0.067876</div>
    <div class="btn">AC</div>
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div class="btn operator">/</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">x</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>
    <div class="btn zero">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
export default {

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .title {
    grid-column: 1 / 5;
    font-weight: lighter;
  }
  .calculator {
    width: 30%;
    margin: 0 auto;
    font-size: 30px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
    font-weight: 100;
  }

  .display {
    grid-column: 1 / 5;
    background: #333;
    color: #fff;
  }

  .zero {
    grid-column: 1 / 3;
  }

  .btn {
    background: #f2f2f2;
    border: 1px solid #ccc;
  }

  .operator {
    background: orange;
    color: #fff;
  }

</style>
