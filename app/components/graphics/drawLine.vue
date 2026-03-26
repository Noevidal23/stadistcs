<template>
  <!-- <Bar :data="data" :options="options" /> -->
  <Line :data="data" :options="options" />
</template>

<script setup>
import {
  Chart as ChartJS,
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend,
} from "chart.js";
import { Line } from "vue-chartjs";

ChartJS.register(
  CategoryScale,
  LinearScale,
  PointElement,
  LineElement,
  Title,
  Tooltip,
  Legend,
);
const props = defineProps(["data", "title"]);
const { ingreso, egreso, situacionFinanciera, disponibilidad } = props.data;

const data = {
  labels: ingreso.map((item) => item.anio),
  datasets: [
    {
      label: "Ingreso",
      backgroundColor: "#005C7A",
      data: ingreso.map((item) => item.MUESTRA),
    },
    {
      label: "Egreso",
      backgroundColor: "#FF8552",
      data: egreso.map((item) => item.MUESTRA),
    },
    {
      label: "Situación Financiera",
      backgroundColor: "#4D6600",
      data: situacionFinanciera.map((item) => item.MUESTRA),
    },
    {
      label: "Disponibilidad",
      backgroundColor: "#1b9aaa",
      data: disponibilidad.map((item) => item.MUESTRA),
    },
  ],
};
const options = {
  responsive: true,
  plugins: {
    title: {
      display: true,
      text: props.title,
    },
  },
};
</script>

<style scoped></style>
