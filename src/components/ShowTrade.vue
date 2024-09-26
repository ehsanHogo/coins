<script setup>
import { computed, onMounted, ref } from "vue";
import TradeCard from "./TradeCard.vue";
const pairs = ref();
const coins = ref();

const getData = async () => {
  const res = await fetch("https://api.exir.io/v2/constants");

  const data = await res.json();

  coins.value = data.coins;
  pairs.value = data.pairs;
};

const findLogo = (name) => {
  let logo;
  const result = Object.entries(coins.value).filter((key, value) => {
    return key[0] === name;
  });

  console.log(result[0][1].logo);

  return result[0][1].logo;
};

onMounted(() => {
  getData();
});
</script>

<template>
  <div>
    <h1 class="tradeList">Trade</h1>

    <div class="pairCards">
      <TradeCard
        v-for="pair in pairs"
        :key="pair.id"
        :pair="pair"
        :pairTwoLogo="findLogo(pair.pair_2)"
        :pairOneLogo="findLogo(pair.pair_base)"
      ></TradeCard>
    </div>
  </div>
</template>

<style scoped>
.pairCards {
  width: 100%;

  display: flex;
  flex-direction: column;
}

.tradeList {
  padding: 1rem 0;
  text-align: center;
}
</style>
