<template>
  <div>
    <!-- INPUTS -->
    <div class="inputs">
      <input
        placeholder="op1"
        type="number"
        ref="op1"
        v-model.number="operand1"
      />
      <input
        placeholder="op2"
        type="number"
        ref="op2"
        v-model.number="operand2"
      />
      = {{ res }}
    </div>
    <!-- / INPUTS -->

    <br />

    <!-- OPERATOR BUTTONS -->
    <div class="buttons">
      <button
        v-for="btn in buttons"
        :key="btn"
        v-bind:title="btn"
        @click="calculate(btn)"
      >
        {{ btn }}
      </button>
    </div>
    <!-- / OPERATOR BUTTONS -->

    <!-- CHECKBOX -->
    <div class="checkbox">
      <input type="checkbox" id="checkbox" v-model="checked" />
      <label for="checkbox">{{ checkbox_text }}</label>
    </div>
    <!-- / CHECKBOX -->

    <br />

    <!-- NUMERIC BUTTONS -->
    <div class="buttons-numbers" v-show="checked">
      <button
        v-for="btnNum in numCollection"
        :key="btnNum"
        v-bind:title="btnNum"
        @click="calculateNum(btnNum)"
      >
        {{ btnNum }}
      </button>
      <br />
      <br />
      <div class="radiobuttons">
        <input
          type="radio"
          id="one"
          name="radio_button"
          value="one"
          v-model="picked"
          @click="focusInput1"
        />
        <label for="one">Focus First Input</label>
        <input
          type="radio"
          id="two"
          name="radio_button"
          value="two"
          v-model="picked"
          @click="focusInput2"
        />
        <label for="two">Focus Second Input</label>
      </div>
    </div>
    <!-- / NUMERIC BUTTONS -->
  </div>
</template>

<script>
export default {
  name: "Calc",
  data: () => ({
    operand1: 0,
    operand2: 0,
    res: 0,
    checked: false,
    buttons: ["+", "-", "*", "/", "**"],
    numCollection: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
    picked: "one",
    checkbox_text: "Open numeric keyboard",
  }),
  methods: {
    calculateNum: function (btnNum) {
      if (this.picked == "one") {
        this.operand1 = btnNum;
      } else {
        this.operand2 = btnNum;
      }
    },
    focusInput1() {
      this.$refs.op1.focus();
    },
    focusInput2() {
      this.$refs.op2.focus();
    },
    calculate(operation = "+") {
      switch (operation) {
        case "**":
          this.exp();
          break;
        case "+":
          this.sum();
          break;
        case "-":
          this.sub();
          break;
        case "*":
          this.mult();
          break;
        case "/":
          this.divide();
          break;
      }
    },
    sum() {
      this.res = this.operand1 + this.operand2;
    },
    sub() {
      this.res = this.operand1 - this.operand2;
    },
    divide() {
      this.res = this.operand1 / this.operand2;
    },
    mult() {
      this.res = this.operand1 * this.operand2;
    },
    exp() {
      this.res = this.operand1 ** this.operand2;
    },
  },
};
</script>

<style scoped lang="scss">
.radiobuttons {
  display: flex;
  justify-content: center;
  label {
    margin-right: 10px;
  }
}
</style>