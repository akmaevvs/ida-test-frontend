<template>
  <div class="inner-container">
    <top-header />
    <section class="content-section">
      <add-form />
      <product-list />
    </section>
  </div>
</template>

<script>
import TopHeader from "@/components/TopHeader.vue";
import AddForm from "@/components/AddForm.vue";
import ProductList from "@/components/ProductList.vue";

export default {
  name: "App",
  components: { TopHeader, AddForm, ProductList }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Source+Sans+Pro&display=swap");
:root {
  --default-text-color: #3f3f3f;
  --placeholder-text-color: #b4b4b4;
  --default-button-text-color: #b4b4b4;
  --input-label-text-color: #49485e;
  --font-size-button-input: 12px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  position: relative;
  background-color: #fffefbcc;
}
input,
button {
  outline: none;
  border: none;
  background: none;
  padding: 0;
  font-family: "Source Sans Pro", Avenir, Helvetica, Arial, sans-serif;
}
input::placeholder {
  font-family: "Source Sans Pro", Avenir, Helvetica, Arial, sans-serif;
  color: var(--placeholder-text-color);
}
#app {
  font-family: "Source Sans Pro", Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #3f3f3f;
}
.inner-container {
  padding: 32px;
  display: flex;
  flex-direction: column;
  gap: 16px;
  width: 100%;
  max-width: 1440px;
  margin: 0 auto;

  & .content-section {
    display: flex;
    justify-content: space-between;
    gap: 16px;
    width: 100%;
    position: relative;
  }
}
</style>
