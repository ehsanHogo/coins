<script setup>
import { computed, onMounted, ref } from "vue";

import CoinCard from "./CoinCard.vue";
const coins = ref();

const filteredCoins = ref();

const getCoins = async () => {
  try {
    const response = await fetch("https://api.exir.io/v2/constants");

    const data = await response.json();

    // console.log(data.coins);

    filteredCoins.value = Object.fromEntries(
      Object.entries(data.coins).slice(0, 30)
    );
  } catch (e) {
    console.log(e);
  }
};

onMounted(() => {
  getCoins();
});
</script>

<template>
  <h1 class="coinsList">Coins List</h1>

  <div class="showCoins">
    <div v-for="coin in filteredCoins" :key="coin.id">
      <CoinCard :name="coin.fullname" :logo-url="coin.logo"></CoinCard>
    </div>
  </div>
</template>

<style scoped>
.showCoins {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-width: 50%;
  gap: 1rem;
}

.coinsList {
  padding-bottom: 1rem;
  color: white;
  text-align: center;
}
</style>
