<script setup>
import { onMounted, ref } from "vue";
import CoinCard from "./components/CoinCard.vue";

const coins = ref();

const getData = async () => {
  try {
    const response = await fetch("https://api.exir.io/v2/constants");

    const data = await response.json();

    console.log(data.coins);

    coins.value = data.coins;
  } catch (e) {
    console.log(e);
  }
};

onMounted(() => {
  getData();
});
</script>

<template>
  <div class="showCoins">
    <div v-for="coin in coins" :key="coin.id">
      <CoinCard :name="coin.fullname" :logo-url="coin.logo"></CoinCard>
    </div>
    <CoinCard></CoinCard>
    <CoinCard></CoinCard>
    <CoinCard></CoinCard>
    <CoinCard></CoinCard>
    <CoinCard></CoinCard>
  </div>
</template>

<style scoped>
.showCoins {
  display: grid;
  grid-template-columns: 1fr 1fr;
  column-width: 50%;
  gap: 1rem;
}
</style>
