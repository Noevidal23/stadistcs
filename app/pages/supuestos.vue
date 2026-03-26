<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Observaciones por Supuestos
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
      <p class="text-center text-gray-500">
        Durante el periodo 2019-2024, las principales irregularidades detectadas
        fueron las siguientes:
      </p>
      <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
        <div
          v-for="(item, index) in irregularidades.irregularidades"
          :key="index"
          class="flex gap-2 text-justify rounded-lg px-2 py-3"
          :class="irregularidades.colors[index]"
        >
          <span class="text-white">{{ index + 1 }}.</span>
          <span class="text-white">{{ item }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import irregularidades from "@/data/irregularidades.json";
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Observaciones por Supuestos",
    to: "",
  },
];
</script>

<style scoped></style>
