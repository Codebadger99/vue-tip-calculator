<template>
  <div class="container">
    <img src="../assets/images/logo.svg" />

    <div class="card">
      <div class="container2">
        <div class="component-1">
          <div class="bill-input">
            <h3>bill</h3>
            <input
              type="text"
              name="amount"
              class="bill"
              placeholder="0"
              v-model="amount"
            />
          </div>

          <div class="select-tip">
            <h3>select tip %</h3>
            <div class="tip-card" ref="tipBtn">
              <div v-for="tip in tips" :key="tip">
                <button class="card-tip" @click="handleClick(tip)">
                  {{ tip }}$
                </button>
              </div>

              <input
                type="text"
                class="card-tip card-tip-input"
                placeholder="custom"
                v-model="input"
              />
            </div>
          </div>
          <div class="people">
            <div class="flex">
              <h4>number of people</h4>
              <h5 v-if="peopleError">Can't be Zero</h5>
            </div>

            <input
              type="text"
              name="people"
              class="people2"
              placeholder="0"
              v-model="people"
              @keyup.enter="submit"
              :class="{ formError: peopleError }"
            />
          </div>
        </div>

        <div class="component-2">
          <div class="amountCard">
            <div class="TipAmount">
              <h3>
                Tip Amount
                <p>/person</p>
              </h3>

              <h1>
                <img src="../assets/images/icon-dollar.svg" class="img" />
                {{ tipAmount }}
              </h1>
            </div>
            <div class="TipTotal">
              <h3>
                Total
                <p>/person</p>
              </h3>

              <h1>
                <img src="../assets/images/icon-dollar.svg" class="img" />
                {{ totalAmount }}
              </h1>
            </div>
            <div class="button">
              <button
                class="reset"
                @click="resetBtn"
                :disabled="tipAmount === '0.00' && totalAmount === '0.00'"
              >
                RESET
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TipCalc",
  data() {
    return {
      amount: "",
      people: "",
      input: "",
      tips: [5, 10, 15, 25, 50],
      tipAmount: "0.00",
      totalAmount: "0.00",
      tip: 0,
      peopleError: false,
    };
  },
  methods: {
    handleClick(num) {
      if (this.tip === num) {
        this.tip = 0;
      } else {
        this.tip = num;
        this.input = "";
      }
    },
    submit() {
      if (this.people.length === 0) {
        this.peopleError = true;
      }

      this.tipAmount = this.tip / this.people || this.input / this.people;
      this.totalAmount = this.amount / this.people;
    },

    resetBtn() {
      (this.tipAmount = "0.00"), (this.totalAmount = "0.00");
      this.amount = "";
      this.people = "";
      this.tip = 0;
    },
  },
};
</script>

<style src="./tipCalc.css"></style>
