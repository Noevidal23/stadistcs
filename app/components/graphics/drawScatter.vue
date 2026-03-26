<template>
  <Scatter :data="chartData" :options="options" />
</template>

<script setup>
const props = defineProps(["data"]);
const { pliegos, promocionesFiscales, pras, aclaraciones } = props.data;
import {
  Chart as ChartJS,
  LinearScale,
  PointElement,
  LineElement,
  Tooltip,
  Legend,
} from "chart.js";
import { Scatter } from "vue-chartjs";
import ChartDataLabels from "chartjs-plugin-datalabels";

ChartJS.register(
  LinearScale,
  PointElement,
  LineElement,
  Tooltip,
  Legend,
  ChartDataLabels,
);
const options = {
  responsive: true,
  plugins: [ChartDataLabels],
  plugins: {
    datalabels: {
      display: false,
    },
  },
};
const chartData = {
  datasets: [
    {
      label: "Pliegos de Observaciones",
      data: pliegos.map((item) => {
        return {
          x: item.anio,
          y: item.total,
        };
      }),
      backgroundColor: "rgba(3, 119, 88, 0.5)",
      borderColor: "rgba(3, 119, 88, 1)",
      borderWidth: 1,
      pointRadius: 11,
    },
    {
      label: `Promociones del Ejercicio de la Facultad de Comprobacion Fiscal`,
      data: promocionesFiscales.map((item) => {
        return {
          x: item.anio,
          y: item.total,
        };
      }),
      backgroundColor: "rgba(27, 154, 170, 0.5)",
      borderColor: "rgba(27, 154, 170, 1)",
      borderWidth: 1,
      pointRadius: 11,
    },
    {
      label: "PRAS",
      data: pras.map((item) => {
        return {
          x: item.anio,
          y: item.total,
        };
      }),
      backgroundColor: "rgba(188, 16, 56, 0.5)",
      borderColor: "rgba(188, 16, 56, 1)",
      borderWidth: 1,
      pointRadius: 11,
    },
    {
      label: "Solicitud de Aclaraciones",
      data: aclaraciones.map((item) => {
        return {
          x: item.anio,
          y: item.total,
        };
      }),
      backgroundColor: "rgba(255, 196, 61, 0.5)",
      borderColor: "rgba(255, 196, 61, 1)",
      borderWidth: 1,
      pointRadius: 11,
    },
  ],
};
</script>

<style scoped></style>
