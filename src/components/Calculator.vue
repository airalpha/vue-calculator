<template>
  <div class="calculator">
    <h1 class="title">Vue Calculator</h1>
    <div class="display">{{ current || 0 }}</div>
    <div class="btn" @click="clear">AC</div>
    <div class="btn" @click="sign">+/-</div>
    <div class="btn" @click="percent">%</div>
    <div class="btn operator" @click="divide">/</div>
    <div class="btn" @click="write(7)">7</div>
    <div class="btn" @click="write(8)">8</div>
    <div class="btn" @click="write(9)">9</div>
    <div class="btn operator" @click="times">x</div>
    <div class="btn" @click="write(4)">4</div>
    <div class="btn" @click="write(5)">5</div>
    <div class="btn" @click="write(6)">6</div>
    <div class="btn operator" @click="minus">-</div>
    <div class="btn" @click="write(1)">1</div>
    <div class="btn" @click="write(2)">2</div>
    <div class="btn" @click="write(3)">3</div>
    <div class="btn operator" @click="plus">+</div>
    <div class="btn zero" @click="write(0)">0</div>
    <div class="btn" @click="dot">.</div>
    <div class="btn operator" @click="equal">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: '',
      operator: null,
      previous: null,
      operatorCliked: false
    }
  },
  methods: {
    clear() {
      this.current = '';
    },

    sign() {
      this.current = this.current * -1;
    },

    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },

    write(number) {
      if(this.operatorCliked) {
        this.current = '';
        this.operatorCliked = false;
      }
      this.current += number.toString();
    },

    dot() {
      //If dot not exist
      if(this.current.indexOf('.') === -1) {
        this.write('.');
      }
    },

    setPrevious() {
      this.previous = this.current;
      this.operatorCliked = true;
    },

    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious()
    },

    times() {
      this.operator = (a, b) => a * b;
      this.setPrevious()
    },

    plus() {
      this.operator = (a, b) => a + b;
      this.setPrevious()
    },

    minus() {
      this.operator = (a, b) => a - b;
      this.setPrevious()
    },

    equal() {
      this.current = `${this.operator(parseFloat(this.previous), parseFloat(this.current))}`;
      this.previous = null;
    }

  }
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
