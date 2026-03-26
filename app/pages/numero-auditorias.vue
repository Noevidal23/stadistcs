<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Número de Auditorías
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <UTabs :items="items" class="w-full" color="neutral">
      <template #ayuntamientos>
        <drawTable
          :data="numeroAuditorias.ayuntamientos"
          :columns="columns"
          title="Ayuntamientos"
        />
        <drawBarStank
          :data="numeroAuditorias.ayuntamientos"
          :dataSet="dataSet"
        />
      </template>

      <template #poderes>
        <drawTable
          :data="numeroAuditorias.poderes"
          :columns="columns"
          title="Poderes del Estado y Organismos Autonomos"
        />
        <drawBarStank :data="numeroAuditorias.poderes" :dataSet="dataSet" />
      </template>
      <template #dif>
        <drawTable
          :data="numeroAuditorias.dif"
          :columns="columns"
          title="DIF"
        />
        <drawBarStank :data="numeroAuditorias.dif" :dataSet="dataSet" />
      </template>
      <template #aguas>
        <drawTable
          :data="numeroAuditorias.aguas"
          :columns="columns"
          title="Sistemas de Agua"
        />
        <drawBarStank :data="numeroAuditorias.aguas" :dataSet="dataSet" />
      </template>
    </UTabs>
  </div>
</template>

<script setup>
import numeroAuditorias from "@/data/numeroAuditorias.json";
import drawBarStank from "@/components/graphics/drawBarStank.vue";
const dataSet = ref("numeroAuditorias");
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
    header: "Año",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },

  {
    accessorKey: "cumplimiento",
    header: "Cumplimiento",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "desempenio",
    header: "Desempeño",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "total",
    header: "Total",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
];
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Número de Auditorías",
  },
];
</script>

<style scoped></style>
