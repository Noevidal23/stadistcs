<template>
  <Doughnut :data="data" :options="options" />
</template>

<script setup>
import {
  Chart as ChartJS,
  ArcElement,
  Tooltip,
  Legend,
  Colors,
} from "chart.js";
import ChartDataLabels from "chartjs-plugin-datalabels";
import { Doughnut } from "vue-chartjs";
ChartJS.register(ArcElement, Tooltip, Legend, Colors, ChartDataLabels);

const props = defineProps(["data"]);
const data = {
  labels: props.data.map((item) => item.anio),
  datasets: [
    {
      backgroundColor: [
        "#4D6600",
        "#037758",
        "#1b9aaa",
        "#bc1038",
        "#ffc43d",
        "#005C7A",
        "#003459",
        "#FF8552",
      ],
      data: props.data.map((item) => (item.porcentaje * 100).toFixed(2)),
    },
  ],
};

const options = {
  responsive: true,
  plugins: [ChartDataLabels],
  plugins: {
    datalabels: {
      formatter: (value, context) => {
        return (
          context.chart.data.labels[context.dataIndex] + "\n" + value + "%"
        );
      },
      color: "#ffffff",
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
    tooltip: {
      callbacks: {
        label: function (context) {
          const adicional = props.data[context.dataIndex].auditados;
          const porcentaje = props.data[context.dataIndex].porcentaje;
          const universo = props.data[context.dataIndex].universo;
          return (
            adicional +
            " Entes Auditados" +
            " de " +
            universo +
            " - Cobertura del " +
            (porcentaje * 100).toFixed(2) +
            "%"
          );
        },
      },
    },
  },
};
</script>

<style scoped></style>
