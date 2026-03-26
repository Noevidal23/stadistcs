<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Acciones y Recomendaciones
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <p class="text-center text-gray-500">
      Derivado de las revisiones a las Cuentas Públicas 2017 a 2024, la
      Auditoría Superior del Estado ha emitido 33,668 acciones y
      recomendaciones; como se aprecian en las siguientes gráficas:
    </p>
    <DrawScatter :data="acciones" />
    <div>
      <h1 class="text-center mt-10">Recomendaciones</h1>
      <drawBarStank
        :data="acciones.recomendaciones"
        dataSet="numeroAuditorias"
      />
    </div>
  </div>
</template>

<script setup>
import DrawScatter from "@/components/graphics/drawScatter.vue";
import drawBarStank from "@/components/graphics/drawBarStank.vue";
import acciones from "@/data/acciones.json";

const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Acciones",
    to: "/acciones",
  },
];
</script>

<style scoped></style>
