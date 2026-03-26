<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Número de Observaciones
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <UTabs :items="items" class="w-full" color="neutral">
      <template #ayuntamientos>
        <drawTable
          :data="numeroObservaciones.ayuntamientos"
          :columns="columns"
        />
        <drawBarStank
          :data="numeroObservaciones.ayuntamientos"
          :dataSet="dataSet"
        />
      </template>
      <template #poderes>
        <drawTable :data="numeroObservaciones.poderes" :columns="columns" />
        <drawBarStank :data="numeroObservaciones.poderes" :dataSet="dataSet" />
      </template>
      <template #dif>
        <drawTable :data="numeroObservaciones.dif" :columns="columns" />
        <drawBarStank :data="numeroObservaciones.dif" :dataSet="dataSet" />
      </template>
      <template #aguas>
        <drawTable :data="numeroObservaciones.aguas" :columns="columns" />
        <drawBarStank :data="numeroObservaciones.aguas" :dataSet="dataSet" />
      </template>
    </UTabs>
  </div>
</template>

<script setup>
import numeroObservaciones from "@/data/numeroObservaciones.json";
import drawTable from "@/components/drawTable.vue";
import drawBarStank from "@/components/graphics/drawBarStank.vue";
const dataSet = ref("numeroObservaciones");
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Número de Observaciones",
  },
];
const items = [
  {
    label: "Ayuntamientos",
    icon: "i-lucide-landmark",
    slot: "ayuntamientos",
  },
  {
    label: "Poderes del Estado",
    icon: "i-lucide-book-marked",
    slot: "poderes",
  },
  {
    label: "DIF",
    icon: "i-lucide-heart-handshake",
    slot: "dif",
  },
  {
    label: "Sistemas de Agua",
    icon: "i-lucide-droplet",
    slot: "aguas",
  },
];

const columns = [
  {
    accessorKey: "anio",
    header: "Ejercicio",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "conImpacto",
    header: "Con Impacto",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "sinImpacto",
    header: "Sin Impacto",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
];
</script>
