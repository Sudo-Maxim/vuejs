<template>
  <div>
    <div>
      <input placeholder="op1" type="number" v-model.number="operand1" />
      <input placeholder="op2" type="number" v-model.number="operand2" />
      = {{ res }}
    </div>
    <div>
      <button @click="sum">+</button>
      <button @click="sub">-</button>
      <button @click="mult">*</button>
      <button @click="divide">/</button>
      <button @click="exp">^</button>
    </div>
    result : {{ res }}
  </div>
</template>

<script>
export default {
  name: "Calc",
  data: () => ({
    operand1: 0,
    operand2: 0,
    res: 0,
  }),
  methods: {
    sum() {
      this.res = this.operand1 + this.operand2;
    },
    sub() {
      this.res = this.operand1 - this.operand2;
    },
    mult() {
      this.res = this.operand1 * this.operand2;
    },
    divide() {
      this.res = Math.floor(this.operand1 / this.operand2);
    },
    exp() {
      this.res = this.operand1 ** this.operand2;
    },
  },
};
</script>