<script setup>
defineProps({
  pairName: String,
  pairOne: String,
  pairTwo: String,
  pairMinPrice: Number,
  pairMaxPrice: Number,
  pairTwoLogo: String,
  pairOneLogo: String,
});
</script>

<template>
  <div class="pairCard">
    <div class="pairName">{{ pairName }}</div>
    <div class="tradeCard">
      <div class="pairOne">
        <img class="coinLogo" :src="pairOneLogo" alt="logo" />
        <p>{{ pairOne }}</p>

        
      </div>

      <div class="pairTwo">
        <img class="coinLogo" :src="pairTwoLogo" alt="logo" />

        <p>{{ pairTwo }}</p>
      </div>

      <div class="pairPrice">{{ pairMinPrice }}$</div>
      <div class="pairPrice">{{ pairMaxPrice }}$</div>
    </div>
  </div>
</template>

<style scoped>
.pairCard {
  background-color: aquamarine;

  padding: 1.5rem;

  border-radius: 20px;

  margin: 1rem;


 
}
.tradeCard {
  display: flex;

  margin: 0.5rem;

  gap: 10rem;
}
.pairOne {
  display: flex;
  width: 25%;
  align-items: center;
  gap: 1rem;

}

.pairTwo {
  width: 25%;
  display: flex;
  align-items: center;
  gap: 1rem;

}

.pairPrice {
  width: 50%;

  display: flex;
  justify-content: start;
  align-items: center;
}

.pairName {
  padding-bottom: 1rem;

  font-weight: bolder;
}

.coinLogo {
  width: 50%;

  display: flex;
  justify-content: end;
}
</style>
