<template>
  <div>
    <div class="skeleton">
      <div class="skeleton-product">
        <img src="" alt="" />
      </div>

      <div class="skeleton-content">
        <h1 class="skeleton-title"></h1>
        <div class="skeleton-detail">
          <p class="skeleton-cateogry"></p>
          <p class="skeleton-rating"></p>
        </div>
        <div class="skeleton-description"></div>
        <div class="skeleton-price"></div>
        <div class="skeleton-button">
          <button class="btn buy">Buy Now</button>
          <button class="btn next">Next Product</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.skeleton-product {
  width: 300px;
  height: 383px;
  animation: pulse 2s infinite ease-in-out;
}

img {
  padding: 30px 0;
}

.skeleton {
  border-radius: 10px;
  width: 1034px;
  display: flex;
  gap: 70px;
  padding: 50px 56px;
  background-color: #ffffff;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
}

.skeleton-content {
  display: flex;
  flex-direction: column;
}

.skeleton-title {
  height: 32px;
  background-color: #94a3b8;
  font-size: 2rem;
  font-weight: 600;
  margin-bottom: 25px;
  animation: pulse 2s infinite ease-in-out;
}
.skeleton-price {
  width: 90px;
  height: 32px;
  background-color: #94a3b8;
  font-size: 1.75rem;
  font-weight: 600;
  margin-bottom: 17px;
  animation: pulse 2s infinite ease-in-out;
}
.skeleton-detail {
  display: flex;
  justify-content: space-between;
  margin-bottom: 11px;
}

.skeleton-detail p:nth-child(1) {
  font-size: 1.125rem;
  font-weight: 400;
  width: 9rem;
  height: 20px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton-detail p:nth-child(2) {
  font-size: 1.125rem;
  font-weight: 400;
  width: 2.5rem;
  height: 20px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton-description {
  flex: 1;
  border-top: 1px solid rgba(0, 0, 0, 0.2);
  border-bottom: 1px solid rgba(0, 0, 0, 0.2);
  padding: 21px 25px 0 0;
  margin-bottom: 16px;
  animation: pulse 2s infinite ease-in-out;
}

.skeleton-button {
  display: flex;
  justify-content: space-evenly;
  gap: 10px;
  padding: 10px;
}
.btn {
  width: 259px;
  border-radius: 4px;
  font-size: 1rem;
  padding: 5px;
  cursor: pointer;
}

.buy {
  background-color: #1E1E1E;
  color: #ffffff;
  border: none;
}

.next {
  background-color: #ffffff;
  color: #1E1E1E;
  border: 3px solid #1E1E1E;
}

@keyframes pulse {
  0% {
    background-color: #94a3b8;
  }

  50% {
    background-color: #cbd5e1;
  }

  100% {
    background-color: #94a3b8;
  }
}
</style>

<script setup></script>
