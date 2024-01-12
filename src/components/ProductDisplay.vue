<template>
  <div>
    <div class="card">
      <div class="card-product">
        <img :src="image" alt="Product" />
      </div>
      <div class="card-content">
        <h1 class="card-title">{{ title }}</h1>
        <div class="card-detail">
          <p class="card-cateogry">{{ category }}</p>
          <p class="card-rating">{{ rating }}/5 </p>
        </div>
        <div class="card-description">{{ description }}</div>
        <div class="card-price">${{ price }}</div>
        <div class="card-button">
          <button class="btn buy">Buy Now</button>
          <button class="btn next" @click="getNextProduct">Next Product</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const emit = defineEmits(['nextProduct'])

const props = defineProps({
  image: {
    type: String,
    default: ''
  }, 
  title: {
    type: String,
    default: ''
  }, 
  category: {
    type: String,
    default: ''
  }, 
  description: {
    type: String,
    default: ''
  }, 
  price: {
    type: String,
    default: ''
  }, 
  rating: {
    type: String,
    default: ''
  },
  titleColor: {
    type: String,
    default: ''
  },
})

const getNextProduct = () => {
  emit('nextProduct')
}
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&family=Quicksand:wght@300;400;500;600;700&display=swap");

* {
  font-family: "Inter", sans-serif;
}

.card-product {
  height: 383px;
}

img {
  height: 383px;
  width: 300px;
  padding: 30px 0;
}

.card {
  border-radius: 10px;
  width: 1034px;
  display: flex;
  gap: 70px;
  padding: 50px 56px;
  background-color: #ffffff;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.card-content {
  display: flex;
  flex-direction: column;
}

.card-title,
.card-price {
  font-size: 1.75rem;
  font-weight: 600;
  color: v-bind(titleColor);
  margin-bottom: 17px;
}

.card-detail {
  display: flex;
  justify-content: space-between;
  margin-bottom: 11px;
}

.card-detail p {
  font-size: 1.125rem;
  font-weight: 400;
}

.card-description {
  flex: 1;
  border-top: 1px solid rgba(0, 0, 0, 0.2);
  border-bottom: 1px solid rgba(0, 0, 0, 0.2);
  padding: 21px 25px 0 0;
  margin-bottom: 16px;
}

.card-button {
  display: flex;
  justify-content: space-evenly;
}
.btn {
  width: 259px;
  border-radius: 4px;
  font-size: 1rem;
  padding: 5px;
  cursor: pointer;
}

.buy {
  background-color: v-bind("titleColor");
  color: #ffffff;
  border: none;
}

.next {
  background-color: #ffffff;
  color: v-bind("titleColor");
  border: 3px solid v-bind("titleColor");
}
</style>
