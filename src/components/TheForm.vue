<template>
  <div id="all">
    <h1>Calculate your monthly payment</h1>
    <h3>Estimate how much you'll pay each month for your new home with our easy-to-use mortgage calculator.</h3>
    <div class="two">
      <form @submit.prevent="calculate">
        <div>
          <div>
            <label for="Home price" class="labels">
              <strong>Home price</strong>
            </label>
          </div>
          <span class="input-symbol-dollar">
            <input
              type="number"
              name="homePrice"
              id="homePrice"
              placeholder="purchase price"
              v-model.number="homePrice"
              step="1000"
              required
            />
          </span>
        </div>
        <div v-if="!validHomePrice" class="warning">Please enter a valid home price greater than 0.</div>
        <div>
          <div>
            <label for="Home price" class="labels">
              <strong>Down payment</strong>
            </label>
          </div>
          <span class="input-symbol-dollar">
            <input
              type="number"
              name="downPayment"
              id="downPayment"
              placeholder="down payment"
              v-model.number="downPayment"
              step="1000"
              required
            />
          </span>
        </div>
        <div v-if="!validDownPayment" class="warning">
          <p>Please enter a valid down payment greater than or equal to 0.</p>
          <p>Most lenders require at least 3.5% of the home price.</p>
        </div>
        <div v-if="!validDownPayment2" class="warning">
          <p>Please enter a down payment less than home price.</p>
          <p>No one wants to pay more than what they have to right?</p>
        </div>
        <div>
          <div>
            <label for="Home price" class="labels">
              <strong>Loan program</strong>
            </label>
          </div>
          <select
            type="check"
            name="loanProgram"
            id="loanProgram"
            placeholder="loan"
            v-model.number="loanProgram"
            required
          >
            <option value="15">15-year-fixed</option>
            <option value="30">30-year-fixed</option>
          </select>
        </div>
        <div>
          <div>
            <label for="Home price" class="labels">
              <strong>Interest rate</strong>
            </label>
          </div>
          <span class="input-rate">
            <input
              type="number"
              name="interestRate"
              id="interestRate"
              placeholder="interest rate in percentage"
              v-model="interestRate"
              step="0.01"
              required
            />
          </span>
        </div>
        <div
          v-if="!validInterestRate"
          class="warning"
        >Please enter a valid interest rate greater than or equal to 0.</div>
        <div>
          <div>
            <label for="taxRate" class="labels">
              <strong>Property tax rate</strong>
            </label>
          </div>
          <span class="input-rate">
            <input
              type="number"
              name="taxRate"
              id="taxRate"
              placeholder="tax rate"
              v-model="taxRate"
              step="0.01"
              required
            />
          </span>
        </div>
        <div
          v-if="!validTaxRate"
          class="warning"
        >Please enter a valid property tax rate greater than or equal to 0.</div>
        <div>
          <div>
            <label for="taxRate" class="labels">
              <strong>Home insurance</strong>
            </label>
          </div>
          <span class="input-symbol-dollar input-home-insurance">
            <input
              type="number"
              name="homeInurance"
              id="homeInsurance"
              placeholder="insurance"
              v-model.number="homeInsurance"
              step="50"
            />
          </span>
        </div>
        <div
          v-if="!validHomeInsurance"
          class="warning"
        >Please enter a valid home insurance greater than or equal to 0.</div>
        <div>
          <div>
            <label for="HOA" class="labels">
              <strong>HOA</strong>
            </label>
          </div>
          <span class="input-symbol-dollar input-HOA">
            <input
              type="number"
              name="HOA"
              id="HOA"
              placeholder="HOA"
              v-model.number="HOA"
              step="5"
            />
          </span>
        </div>
        <div v-if="!validHOA" class="warning">Please enter a valid HOA greater than or equal to 0.</div>
      </form>
      <div class="dataviz">
        <h2>
          <strong>Your payment breakdown</strong>
        </h2>
        <p>Monthly payment: ${{Math.round(dataObj.monthlyPayment)}}</p>
        <p>Principal and interest: ${{Math.round(dataObj.principalAndInterest)}}</p>
        <p>Taxes: ${{Math.round(dataObj.taxes/12)}}</p>
        <p>HOA: ${{ Math.round(dataObj.HOA) ? Math.round(dataObj.HOA) : 0 }}</p>
        <p>Insurance: ${{Math.round(dataObj.insurance/12)}}</p>
        <p>Estimated PMI: ${{Math.round(dataObj.PMI) ? Math.round(dataObj.PMI) : 0}}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showAdvanced: false,
      homePrice: 200_000,
      downPayment: 40_000,
      loanProgram: 15,
      interestRate: 3.0,
      i: this.interestRate / 1200,
      n: this.loanProgram * 12,
      taxRate: 3.0,
      propertyTax: null,
      homeInsurance: 500,
      HOA: 50,
      principalAndInterest: null,
      monthlyPayment: null,
      PMI: null,
      dataObj: {
        principalAndInterest: this.principalAndInterest,
        monthlyPayment: this.monthlyPayment,
        taxes: this.propertyTax,
        HOA: this.HOA,
        insurance: this.homeInsurance,
        PMI: this.PMI
      },
      validHomePrice: true,
      validDownPayment: true,
      validDownPayment2: true,
      validInterestRate: true,
      validTaxRate: true,
      validHomeInsurance: true,
      validHOA: true
    };
  },
  methods: {
    toggle() {
      this.showAdvanced = !this.showAdvanced;
    },
    calculate() {
      if (this.homePrice <= 0) {
        this.validHomePrice = false;
      }

      if (this.downPayment > this.homePrice) {
        this.validDownPayment2 = false;
      }

      if (this.downPayment < 0) {
        this.validDownPayment = false;
      }

      if (this.interestRate < 0) {
        this.validInterestRate = false;
      }

      if (this.taxRate < 0) {
        this.validTaxRate = false;
      }

      if (this.homeInsurance < 0) {
        this.validHomeInsurance = false;
      }

      if (this.HOA < 0) {
        this.validHOA = false;
      }

      if (this.HOA === "") {
        this.validHOA = false;
      }

      if (this.checkFields) {
        this.validHomePrice = true;
        this.validDownPayment = true;
        this.validDownPayment2 = true;
        this.validInterestRate = true;
        this.validTaxRate = true;
        this.validHomeInsurance = true;
        this.validHOA = true;

        this.i = this.interestRate / 1200;

        this.n = this.loanProgram * 12;

        this.propertyTax = (this.homePrice * this.taxRate) / 100;

        this.principalAndInterest =
          ((this.homePrice - this.downPayment) *
            (this.i * Math.pow(this.i + 1, this.n))) /
          (Math.pow(1 + this.i, this.n) - 1);

        this.monthlyPayment =
          this.principalAndInterest +
          this.homeInsurance / 12 +
          this.HOA +
          this.propertyTax / 12;

        this.dataObj.principalAndInterest = this.principalAndInterest;
        this.dataObj.monthlyPayment = this.monthlyPayment;
        this.dataObj.taxes = this.propertyTax;
        this.dataObj.HOA = this.HOA;
        this.dataObj.insurance = this.homeInsurance;
      } else {
        this.dataObj.principalAndInterest = 0;
        this.dataObj.monthlyPayment = 0;
        this.dataObj.taxes = 0;
        this.dataObj.HOA = 0;
        this.dataObj.insurance = 0;
        this.dataObj.PMI = 0;
      }
    },
    calcPMI() {
      if (this.checkPMI && this.checkFields) {
        this.dataObj.PMI = (this.homePrice - this.downPayment) / 2000;
      } else {
        this.dataObj.PMI = 0;
      }
    }
  },
  computed: {
    checkPMI() {
      return this.downPayment < 0.2 * this.homePrice;
    },
    checkFields() {
      return (
        this.homePrice > 0 &&
        this.downPayment > 0 &&
        this.downPayment < this.homePrice &&
        this.interestRate >= 0 &&
        this.taxRate >= 0 &&
        this.homeInsurance >= 0 &&
        this.HOA >= 0 &&
        this.HOA !== ""
      );
    }
  },
  mounted() {
    this.calculate();
    this.calcPMI();
  },
  updated() {
    this.calculate();
    this.calcPMI();
  }
};
</script>

<style scoped>
p {
  font-size: 1rem;
}

#all {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

form {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  margin: 3rem 1rem 1rem 0rem;
  width: 30%;
  min-width: 30rem;
}

.warning {
  color: red;
  font-weight: bolder;
}

.dataviz {
  margin: 3rem 1rem 1rem 0rem;
}

div {
  margin-bottom: 0.3rem;
}

.two {
  display: flex;
  flex-direction: row;
}

input,
select {
  border-radius: 6px;
  font-size: 1rem;
  padding: 0.4rem 0.4rem;
  background-color: rgb(249, 249, 251);
}

h1 {
  margin-top: 3rem;
  text-align: center;
}

.dataviz p {
  font-weight: bolder;
}

.input-symbol-dollar {
  position: relative;
}

.input-symbol-dollar input {
  padding-left: 18px;
}

.input-symbol-dollar:before {
  position: absolute;
  top: 0;
  content: "$";
  left: 5px;
  font-weight: bolder;
}

.input-home-insurance {
  position: relative;
}

.input-home-insurance input {
  padding-left: 18px;
}

.input-home-insurance:after {
  position: absolute;
  top: 0;
  content: "/year";
  right: 25px;
  font-weight: lighter;
}

.input-HOA {
  position: relative;
}

.input-HOA input {
  padding-left: 18px;
}

.input-HOA:after {
  position: absolute;
  top: 0;
  content: "/month";
  right: 25px;
  font-weight: lighter;
}

.input-rate {
  position: relative;
}

.input-rate input {
  padding-left: 10px;
}

.input-rate:after {
  position: absolute;
  top: 0;
  content: "%";
  right: 20px;
  font-weight: lighter;
}
</style>