<script setup>
import { onMounted, ref } from "vue";
import ShowCoins from "./components/ShowCoins.vue";

import ShowTrade from "./components/ShowTrade.vue";
</script>

<template>
  <div>
    <ShowCoins></ShowCoins>
  </div>

  <div>
    <ShowTrade></ShowTrade>
  </div>
</template>

<style scoped></style>
