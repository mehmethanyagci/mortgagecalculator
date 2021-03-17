<template>
  <div>
    <h1>visualization component</h1>
    <p>monthly payment: ${{Math.round(dataObj.monthlyPayment)}}</p>
    <p>principal and interest: ${{Math.round(dataObj.principalAndInterest)}}</p>
    <p>taxes: ${{Math.round(dataObj.taxes/12)}}</p>
    <p>HOA: ${{Math.round(dataObj.hoa)}}</p>
    <p>insurance: ${{Math.round(dataObj.insurance/12)}}</p>
    <div id="mydataviz"></div>
  </div>
</template>

<script>
//import * as d3 from "d3";

export default {
  props: ["dataObj"]
};
</script>

<style scoped>
div {
  width: 30rem;
  min-width: 30rem;
  font-size: 1.2rem;
  margin: 2rem;
}
</style>