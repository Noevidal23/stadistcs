<template>
  <PolarArea :data="data" :options="options" v-if="dataSet === 'monto'" />
  <PolarArea :data="federalData" :options="options" v-else />
</template>

<script setup>
import {
  Chart as ChartJS,
  RadialLinearScale,
  ArcElement,
  Tooltip,
  Legend,
} from "chart.js";
import { PolarArea } from "vue-chartjs";
ChartJS.register(RadialLinearScale, ArcElement, Tooltip, Legend);
const props = defineProps(["data", "title", "dataSet"]);

const options = {
  responsive: true,
  scales: {
    r: {
      pointLabels: {
        display: true,
        centerPointLabels: true,
        font: {
          size: 18,
        },
      },
    },
  },
  plugins: {
    legend: {
      position: "top",
    },
    title: {
      display: true,
      text: props.title,
    },
  },
};

const federalData = {
  labels: props.data.map((item) => item.ente),
  datasets: [
    {
      data: props.data.map((item) => item.total),
      backgroundColor: [
        "rgba(255, 99, 132, 0.5)",
        "rgba(54, 162, 235, 0.5)",
        "rgba(255, 206, 86, 0.5)",
        "rgba(75, 192, 192, 0.5)",
        "rgba(153, 102, 255, 0.5)",
        "rgba(255, 159, 64, 0.5)",
      ],
      borderColor: [
        "rgba(255, 99, 132, 1)",
        "rgba(54, 162, 235, 1)",
        "rgba(255, 206, 86, 1)",
        "rgba(75, 192, 192, 1)",
        "rgba(153, 102, 255, 1)",
        "rgba(255, 159, 64, 1)",
      ],
      borderWidth: 1,
    },
  ],
};
const data = {
  labels: props.data.map((item) => item.anio),
  datasets: [
    {
      label: props.title,
      data: props.data.map((item) => item.monoto),
      backgroundColor: [
        "rgba(255, 99, 132, 0.5)",
        "rgba(54, 162, 235, 0.5)",
        "rgba(255, 206, 86, 0.5)",
        "rgba(75, 192, 192, 0.5)",
        "rgba(153, 102, 255, 0.5)",
        "rgba(255, 159, 64, 0.5)",
      ],
      borderColor: [
        "rgba(255, 99, 132, 1)",
        "rgba(54, 162, 235, 1)",
        "rgba(255, 206, 86, 1)",
        "rgba(75, 192, 192, 1)",
        "rgba(153, 102, 255, 1)",
        "rgba(255, 159, 64, 1)",
      ],
      borderWidth: 1,
    },
  ],
};
</script>

<style scoped></style>
