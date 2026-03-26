<template>
  <div v-if="props.dataSet === 'numeroAuditorias'">
    <Bar :data="data" :options="options" />
  </div>
  <div v-else-if="props.dataSet === 'numeroObservaciones'">
    <Bar :data="dataObservaciones" :options="options" />
  </div>
</template>

<script setup>
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";
import { Bar } from "vue-chartjs";
import ChartDataLabels from "chartjs-plugin-datalabels";

ChartJS.register(
  CategoryScale,
  LinearScale,
  BarElement,
  Title,
  Tooltip,
  Legend,
  ChartDataLabels,
);
const props = defineProps(["data", "title", "dataSet"]);
const data = {
  labels: props.data.map((item) => item.anio),
  datasets: [
    {
      label: "Cumplimiento",
      backgroundColor: "#005C7A",
      data: props.data.map((item) => item.cumplimiento),
    },
    {
      label: "Desempeño",
      backgroundColor: "#FF8552",
      data: props.data.map((item) => item.desempenio),
    },
  ],
};
const dataObservaciones = {
  labels: props.data.map((item) => item.anio),
  datasets: [
    {
      label: "Con Impacto",
      backgroundColor: "#005C7A",
      data: props.data.map((item) => item.conImpacto),
    },
    {
      label: "Sin Impacto",
      backgroundColor: "#FF8552",
      data: props.data.map((item) => item.sinImpacto),
    },
  ],
};
const options = {
  responsive: true,
  plugins: [ChartDataLabels],
  plugins: {
    title: {
      display: true,
      text: props.title,
    },
    datalabels: {
      labels: {
        title: {
          font: {
            weight: "bold",
          },
        },
        value: {
          color: "#ffffff",
        },
      },
    },
  },
  scales: {
    x: {
      stacked: true,
    },
    y: {
      stacked: true,
    },
  },
};
</script>

<style scoped></style>
