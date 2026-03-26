<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Número de Entes Auditados
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <UTabs :items="items" class="w-full" color="neutral">
      <template #ayuntamientos>
        <drawTable
          :data="entes.ayuntamientos"
          :columns="columns"
          title="Ayuntamientos"
        />
        <drawDoughnut :data="entes.ayuntamientos" class="w-1/3" />
      </template>

      <template #poderes>
        <drawTable
          :data="entes.Poderes"
          :columns="columns"
          title="Poderes del Estado y Organismos Autonomos"
        />
        <drawDoughnut :data="entes.Poderes" />
      </template>
      <template #dif>
        <drawTable :data="entes.dif" :columns="columns" title="DIF" />
        <drawDoughnut :data="entes.dif" />
      </template>
      <template #aguas>
        <drawTable
          :data="entes.aguas"
          :columns="columns"
          title="Sistemas de Agua"
        />
        <drawDoughnut :data="entes.aguas" />
      </template>
    </UTabs>
  </div>
</template>

<script setup>
import entes from "@/data/entes.json";
import drawDoughnut from "@/components/graphics/drawDoughnut.vue";
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Número de Entes Auditados",
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
    header: "Año",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "universo",
    header: "Universo",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "auditados",
    header: "Auditados",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "porcentaje",
    header: "Porcentaje",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("porcentaje"));
      return new Intl.NumberFormat("es-MX", {
        style: "percent",
        minimumFractionDigits: 2,
        maximumFractionDigits: 2,
      }).format(amount);
    },
  },
];
</script>

<style scoped></style>
