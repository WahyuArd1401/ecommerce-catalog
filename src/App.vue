<template>
  <main>
    <div class="background-product">
    </div>
    <div class="product">
      <template v-if="!isLoading">
        <template
          v-if="
            products.category === `men's clothing` ||
            products.category === `women's clothing`
          "
        >
          <ProductDisplay
            :image="products.image"
            :title="products.title"
            :category="products.category"
            :rating="JSON.stringify(parseFloat(products.rating?.rate))"
            :description="products.description"
            :price="JSON.stringify(parseFloat(products.price))"
            :title-color="getGenderColor(products.category)"
            @next-product="handleNextProduct"
          />
        </template>
        <template v-else>
          <UnavailableDisplay @next-product="handleNextProduct" />
        </template>
      </template>
  
      <SkeletonDisplay v-else />
    </div>
  </main>
</template>

<script setup>
import ProductDisplay from "./components/ProductDisplay.vue";
import SkeletonDisplay from "./components/SkeletonDisplay.vue";
import UnavailableDisplay from "./components/UnavailableDisplay.vue";

import axios from "axios";
import { ref, onBeforeMount } from "vue";

const products = ref([]);
const currentIndex = ref(1);
const isLoading = ref(false);
//Mendapatkan Data
const getProducts = () => {
  isLoading.value = true;
  setTimeout(() => {
    const urlAPI = `https://fakestoreapi.com/products/${currentIndex.value}`;
    axios
      .get(urlAPI)
      .then((response) => {
        products.value = response.data;
      })
      .catch((error) => {
        console.error("Error fetching data:", error);
      })
      .finally(() => {
        isLoading.value = false;
      });
  }, 1000);
};

//Mendapatkan Produk Berikutnya
const handleNextProduct = () => {
  currentIndex.value = (currentIndex.value + 1) % 20;
  getProducts();
  
};

// Mendapatkan warna judul berdasarkan kategori
const getGenderColor = (category) => {
  return category === "men's clothing"
    ? "#002772"
    : category === "women's clothing"
    ? "#720060"
    : "#1E1E1E";
};

const getBackgroundColor = (category) => {
  return category === "men's clothing"
    ? "#D6E6FF"
    : category === "women's clothing"
    ? "#FDE2FF"
    : "#DCDCDC";
};

onBeforeMount(() => {
  getProducts();
});
</script>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background-color: #ffffff;
}

.background-product {
  position: absolute;
  top: 0;
  width: 100%;
  height: 450px;
  background-color: v-bind("getBackgroundColor(products.category)");
  background-image: url('./assets/bg-pattern.svg');
}

.product {
  z-index: 99;
}
</style>
