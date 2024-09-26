<script setup>
import { onMounted, ref } from "vue";
import CoinCard from "./components/CoinCard.vue";

const coins = ref();

const getData = async () => {
  try {
    const response = await fetch("https://api.exir.io/v2/constants");

    const data = await response.json();

    console.log(data.coins);
    console.log(data);

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
    <div v-for="coin in Object.values(coins).slice(0, 30)" :key="coin.id">
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
</style>
