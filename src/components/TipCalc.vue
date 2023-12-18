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
              <div v-for="tip in tips" :key="tip.id">
                <button
                  class="card-tip"
                  @click="handleClick(tip)"
                  :class="{ cl: tip.isColoured }"
                  ref="btn"
                >
                  {{ tip.tip }}$
                </button>
              </div>

              <input
                type="number"
                class="card-tip card-tip-input"
                placeholder="custom"
                v-model="input"
                ref="input"
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
      tips: [
        {
          id: 1,
          tip: 5,
          isColoured: false,
        },
        {
          id: 2,
          tip: 10,
          isColoured: false,
        },
        {
          id: 3,
          tip: 15,
          isColoured: false,
        },
        {
          id: 4,
          tip: 25,
          isColoured: false,
        },
        {
          id: 5,
          tip: 50,
          isColoured: false,
        },
      ],
      tipAmount: "0.00",
      totalAmount: "0.00",
      tip: 0,
      peopleError: false,
      tipPercentage: 0,
      totalamount: 0,
      btnValue: 0,
    };
  },
  methods: {
    handleClick(tip) {
      this.btnValue = tip.tip;

      if ((tip.isColoured = !tip.isColoured)) {
        this.$refs.input.disabled = true;
      } else {
        this.$refs.input.disabled = false;
      }
    },
    submit() {
      if (this.people.length === 0) {
        this.peopleError = true;
      }
      if (this.btnValue) {
        this.tipPercentage = this.btnValue / 100;
        this.tip = this.amount * this.tipPercentage;
        this.totalamount = parseInt(this.amount) + this.tip;
        this.tipAmount = (this.tip / this.people).toFixed(2);
        this.totalAmount = this.totalamount / this.people;
      } else {
        this.tipPercentage = this.input / 100;
        this.tip = this.amount * this.tipPercentage;
        this.totalamount = parseInt(this.amount) + this.tip;
        this.tipAmount = (this.tip / this.people).toFixed(2);
        this.totalAmount = this.totalamount / this.people;
      }
    },

    resetBtn() {
      this.tipAmount = "0.00";
      this.totalAmount = "0.00";
      this.amount = "";
      this.people = "";
      this.tip = 0;
      this.input = "";
    },
  },
};
</script>

<style src="./tipCalc.css"></style>
