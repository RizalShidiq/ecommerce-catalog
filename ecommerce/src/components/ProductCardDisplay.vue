<script>
import ProductUnavailableView from "./ProductUnavailableView.vue";

const API_BASE_URL = "https://fakestoreapi.com/products/";
const MAX_PRODUCTS = 20;

export default {
  name: "ProductCardDisplay",
  components: {
    ProductUnavailableView,
  },
  data() {
    return {
      currentProductId: 0,
      currentProduct: {},
      loading: false,
      productAvailable: false,
      currentTheme: "",
      placeholderImage:
        "https://placehold.co/300x380/EFEFEF/AAAAAA?text=Produk",
    };
  },
  computed: {
    ratingText() {
      const rate = this.currentProduct.rating?.rate || 0;
      const count = this.currentProduct.rating?.count || 0;
      return `${rate.toFixed(1)}/5`;
    },
    fullStars() {
      return Math.round(this.currentProduct.rating?.rate || 0);
    },
    formattedPrice() {
      return (this.currentProduct.price || 0).toFixed(2);
    },
    starBorderColor() {
      return this.currentTheme === "men"
        ? "#002772"
        : this.currentTheme === "women"
        ? "#720060"
        : "#002772";
    },
    starFillColor() {
      return this.currentTheme === "men"
        ? "#002772"
        : this.currentTheme === "women"
        ? "#720060"
        : "#002772";
    },
  },
  methods: {
    async fetchProduct(id) {
      this.loading = true;
      this.productAvailable = false;

      try {
        const response = await fetch(`${API_BASE_URL}${id}`);
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }
        const product = await response.json();

        if (product && product.category) {
          const categoryLower = product.category.toLowerCase();
          if (
            categoryLower === "men's clothing" ||
            categoryLower === "women's clothing"
          ) {
            this.currentProduct = product;
            this.productAvailable = true;
            this.updatePageTheme(categoryLower);
          } else {
            this.currentProduct = {};
            this.updatePageTheme("unavailable");
          }
        } else {
          this.currentProduct = {};
          this.updatePageTheme("unavailable");
        }
      } catch (error) {
        console.error("Error fetching product:", error);
        this.currentProduct = {};
        this.updatePageTheme("unavailable");
      } finally {
        this.loading = false;
      }
    },
    updatePageTheme(category) {
      document.body.classList.remove(
        "mens-theme-bg",
        "womens-theme-bg",
        "unavailable-theme-bg"
      );

      if (category === "men's clothing") {
        this.currentTheme = "men";
        document.body.classList.add("mens-theme-bg");
      } else if (category === "women's clothing") {
        this.currentTheme = "women";
        document.body.classList.add("womens-theme-bg");
      } else {
        this.currentTheme = "unavailable";
        document.body.classList.add("unavailable-theme-bg");
      }
    },
    handleNextProduct() {
      this.currentProductId++;
      if (this.currentProductId > MAX_PRODUCTS) {
        this.currentProductId = 1;
      }
      this.fetchProduct(this.currentProductId);
    },
    handleBuyNow() {
      alert(`Buy: ${this.currentProduct.title}`);
    },
  },
  mounted() {
    this.handleNextProduct();
  },
};
</script>

<template>
  <div
    class="product-card-wrapper"
    :class="{
      'mens-theme': currentTheme === 'men',
      'womens-theme': currentTheme === 'women',
      'unavailable-theme': currentTheme === 'unavailable',
    }"
  >
    <div v-if="loading" class="loader-container">
      <div class="loader"></div>
    </div>

    <div v-if="!loading && productAvailable" class="product-content">
      <div class="product-image-container">
        <img
          :src="currentProduct.image || placeholderImage"
          :alt="currentProduct.title"
          class="product-image"
        />
      </div>
      <div class="product-details">
        <h1 class="product-title">{{ currentProduct.title }}</h1>
        <div class="product-category-rating">
          <p class="product-category">{{ currentProduct.category }}</p>
          <div class="rating">
            <span class="rating-text">{{ ratingText }}</span>
            <div class="rating-stars">
              <div
                v-for="i in 5"
                :key="i"
                class="star"
                :style="{
                  borderColor: starBorderColor,
                  backgroundColor: i <= fullStars ? starFillColor : '#FFFFFF',
                }"
              ></div>
            </div>
          </div>
        </div>
        <p class="product-description">{{ currentProduct.description }}</p>
        <div class="product-price-line">
          <p class="product-price">${{ formattedPrice }}</p>
        </div>
        <div class="buttons-container">
          <button
            class="btn buy-now-btn"
            @click="handleBuyNow"
            :disabled="loading"
          >
            Buy now
          </button>
          <button
            class="btn next-product-btn"
            @click="handleNextProduct"
            :disabled="loading"
          >
            Next product
          </button>
        </div>
      </div>
    </div>

    <ProductUnavailableView
      v-if="!loading && !productAvailable"
      @next-product="handleNextProduct"
      :loading="loading"
    />
  </div>
</template>

<style scoped></style>