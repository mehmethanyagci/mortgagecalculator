<template>
  <div>
    <the-header></the-header>
    <the-form></the-form>
    <the-application></the-application>
    <the-info></the-info>
    <the-footer></the-footer>
  </div>
</template>

<script>
import TheForm from "./components/TheForm.vue";
import TheHeader from "./components/TheHeader.vue";
import TheInfo from "./components/TheInfo.vue";
import TheApplication from "./components/TheApplication.vue";
import TheFooter from "./components/TheFooter.vue";

export default {
  components: {
    TheForm,
    TheHeader,
    TheInfo,
    TheApplication,
    TheFooter
  },
  data() {
    return {
      dataObj: {
        principalAndInterest: null,
        monthlyPayment: null,
        taxes: null,
        hoa: null,
        insurance: null
      }
    };
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Quicksand:wght@400;500&display=swap");

* {
  box-sizing: border-box;
}

html {
  font-family: "Quicksand", sans-serif;
  min-width: 50rem;
}

body {
  margin: 0;
}
</style>
