<script setup>
defineProps({
  name: String,
  logoUrl: String,
});
</script>

<template>
  <div class="coinCard">
    <div class="coinName">{{ name }}</div>

    <div class="coinLogo">
      <img class="logoPic" :src="logoUrl" alt="Coin Logo" />
    </div>
  </div>
</template>

<style scoped>
.coinCard {
  width: 100%;

  display: flex;

  justify-content: center;
  align-items: center;
  background-color: rgb(127, 197, 255);
  padding: 1rem 2rem;
  border-radius: 10px;
}

.coinName {
  width: 50%;
}

.coinLogo {
  width: 50%;

  display: flex;
  justify-content: end;
}

.logoPic {
  width: 25%;
}
</style>
