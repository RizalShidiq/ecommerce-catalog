<script>
export default {
  name: "ProductUnavailableView",
  props: {
    loading: {
      type: Boolean,
      default: false,
    },
  },
};
</script>

<template>
  <div class="unavailable-product-view">
    <div class="sad-face">:(</div>
    <p class="unavailable-text">This product is unavailable to show</p>
    <button
      class="btn next-product-btn"
      @click="$emit('next-product')"
      :disabled="loading"
    >
      Next product
    </button>
  </div>
</template>

<style scoped>
.unavailable-product-view {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  text-align: center;
}
</style>
