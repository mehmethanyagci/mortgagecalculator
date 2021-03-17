<template>
  <div>
    <p>Ready to call this home?</p>
    <a
      class="button"
      href="https://homefinancing.chase.com/PSPurchase?SourceCode=ES155&jp_cmp=hf/Chase+Mortgage_Brand_Exact_MTG_SEM_US_NA_Standard_NA/sea/p25024238485/Chase+Application&gclid=CjwKCAiAp4KCBhB6EiwAxRxbpDSoLDnOCkKyOTS9gYbaLFro_BIOB7C8QZyl5YQj_JLU00Xnv8nZhhoCVhUQAvD_BwE&gclsrc=aw.ds"
      target="blank"
    >Get pre-approved</a>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  margin-top: 4rem;
  padding: 1rem;
  background-color: rgb(249, 249, 251);
  width: 100%;
  height: 15rem;
}

a.button {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgb(25, 71, 257);
  border-radius: 6px;
  font-size: 1.2em;
  color: white;
  text-decoration: none;
  height: 3rem;
  width: 15rem;
}

a.button:hover {
    background-color: tomato;
}

p {
  font-size: 2rem;
}
</style>