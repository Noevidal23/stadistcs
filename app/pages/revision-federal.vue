<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Revisión a los Recursos Federales
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <drawPolarArea
      :data="recursoFederal"
      title="Recurso Federal"
      dataSet="Federal"
    />
  </div>
</template>

<script setup>
import { recursoFederal } from "@/data/recursoFederal.json";
import drawPolarArea from "@/components/graphics/drawPolarArea.vue";
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Recurso Federal",
    to: "",
  },
];
</script>

<style scoped></style>
