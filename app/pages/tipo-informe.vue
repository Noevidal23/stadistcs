<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Tipo de Informe
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <p class="text-center text-gray-500">
      Como resultado de las revisiones a las Cuentas Públicas correspondientes
      al periodo 2017-2024, la Auditoría Superior del Estado ha emitido un total
      de 1,606 Informes Individuales. De estos, 1,485 derivaron de auditorías de
      cumplimiento, y 121 de auditorías de desempeño, como se muestra en la
      siguiente gráfica.
    </p>
    <drawBarStank :data="tipoInforme.informe" dataSet="numeroAuditorias" />
  </div>
</template>

<script setup>
import tipoInforme from "@/data/tipoInforme.json";
import drawBarStank from "@/components/graphics/drawBarStank.vue";
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Tipo de Informe",
  },
];
</script>

<style scoped></style>
