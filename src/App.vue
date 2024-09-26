<script setup>
import { Bar } from "vue-chartjs";
import {
  Chart,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js/auto";

// Chart.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

const chartData = {
  labels: ["January", "February", "March"],
  datasets: [{ data: [40, 20, 12] }],
};

const chartOptions = {
  responsive: true,
};
</script>

<template>
  < <Bar id="my-chart-id" :options="chartOptions" :data="chartData" />
</template>

<style scoped></style>
