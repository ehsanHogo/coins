<script setup>
import { onMounted, ref } from "vue";
import TradeCard from "./TradeCard.vue";
const pairs = ref();
const getPairs = async () => {
  const res = await fetch("https://api.exir.io/v2/constants");

  const data = await res.json();

  console.log(data);

  pairs.value = data.pairs;

  console.log(pairs.value);
};

onMounted(() => {
  getPairs();
});
</script>

<template>
  <div>
    <h1 class="tradeList">Trade</h1>

    <div class="pairCard">
      <TradeCard></TradeCard>
    </div>
  </div>
</template>

<style scoped>
.pairName {
}
.pairCard {
  width: 100%;

  background-color: aquamarine;

  padding: 2rem;
  border-radius: 20px;
}

.tradeList {
  padding: 1rem 0;

  text-align: center;
}
</style>
