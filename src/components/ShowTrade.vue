<script setup>
import { computed, onMounted, ref } from "vue";
import TradeCard from "./TradeCard.vue";
const pairs = ref();

const coins = ref();
const getData = async () => {
  const res = await fetch("https://api.exir.io/v2/constants");

  const data = await res.json();

  console.log(data);

  coins.value = data.coins;
  pairs.value = data.pairs;
  console.log("find : ", pairs.value);
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

    <div v-for="pair in pairs" :key="pair.id" class="pairCards">
      <TradeCard
        :pairName="pair.name"
        :pairOne="pair.pair_base"
        :pairTwo="pair.pair_2"
        :pairTwoLogo="findLogo(pair.pair_2)"
        :pairOneLogo="findLogo(pair.pair_base)"
        :pairMinPrice="pair.min_price"
        :pairMaxPrice="pair.max_price"
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
  color: white;
  text-align: center;
}
</style>
