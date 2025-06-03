<script>
import ProductCardDisplay from "./components/ProductCardDisplay.vue";

export default {
  name: "App",
  components: {
    ProductCardDisplay,
  },
};
</script>

<template>
  <div id="app">
    <div class="container">
      <ProductCardDisplay />
    </div>
  </div>
</template>

<style module>
body {
  background-image: url("./assets/bg-pattern.png");
  position: relative;
  z-index: -1;
}
</style>
