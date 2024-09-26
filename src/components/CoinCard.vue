<script setup>
defineProps({
  name: String,
  logoUrl: String,
});
</script>

<template>
  <div class="coinCard">
    <div class="coinName">{{ name }} name of coin</div>

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
  background-color: aquamarine;
  padding: 1rem 1rem;
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
