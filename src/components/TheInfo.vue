<template>
  <div id="all">
    <hr />
    <h1>Need help?</h1>
    <p id="more">The more information you can provide, the more accurate your estimate will be.</p>
    <div>
      <div class="row">
        <div class="element">
          <h3>Home Price</h3>
          <p>Enter the purchase price of the home you want to buy. You can also enter the amount that you think you will offer.</p>
        </div>
        <div class="element">
          <h3>Down payment</h3>
          <p>Most home loans require a down payment of at least 3%. A higher down payment will lower your monthly payment.</p>
        </div>
        <div class="element">
          <h3>Loan Program</h3>
          <p>Your loan program can affect your interest rate and monthly payments. Choose from 30-year fixed or 15-year fixed in the calculator.</p>
        </div>
      </div>
      <div class="row">
        <div class="element">
          <h3>Interest Rate</h3>
          <p>Your rate will vary based on factors like credit scores and down payment amount.</p>
        </div>
        <div class="element">
          <h3>Property Tax</h3>
          <p>The mortgage payment calculator includes estimated property taxes based on the home's value.</p>
        </div>
        <div class="element">
          <h3>Home Insurance</h3>
          <p>Home insurance or homeowners insurance is typically required by lenders.</p>
        </div>
      </div>
    </div>
    <hr />
    <div id="white-space"></div>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>

#more {
  text-align: center;
  margin: 0.5rem;
}

p {
  margin: 0;
}
h1 {
  text-align: center;
  font-weight: bold;
}

h3 {
  font-size: 1.2rem;
  margin: 0;
  padding: 0;
}

a {
  text-align: right;
  display: flex;
  justify-content: center;
  align-items: center;
}

.row {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  margin: 2rem;
}

.element {
  display: grid;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  box-shadow: 1px 1px 3px grey;
  margin: 0 1rem;
  padding: 0.2rem;
  width: 20rem;
  height: 10rem;
}

#all {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: space-around;
}

#white-space {
  background-color: white;
  width: 100%;
  height: 8rem;
}
</style>