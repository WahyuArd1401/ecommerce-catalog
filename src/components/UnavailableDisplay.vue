<template>
  <div>
    <div class="unavailable">
      <p>This product is not available to show</p>
      <button class="btn next" @click="getNextProduct">Next Product</button>
    </div>
  </div>
</template>

<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['nextProduct'])

const getNextProduct = () => {
  emit('nextProduct')
}
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@500&family=Quicksand:wght@300;400;500;600;700&display=swap");
.unavailable {
  border-radius: 10px;
  width: 1034px;
  height: 483px;
  font-family: 'Inter', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: #ffffff;
  background-image: url('../assets/sad-face.svg');
  background-repeat: no-repeat;
  background-size: contain;
  background-position: 70px 40px;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.btn {
  width: 400px;
  border-radius: 4px;
  font-size: 1rem;
  padding: 5px;
  cursor: pointer;
}

.next {
  background-color: #ffffff;
  color: rgb(0, 0, 0);
  border: 3px solid rgb(0, 0, 0);
}

p {
  margin-bottom: 10px;
}

</style>
