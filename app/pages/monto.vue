<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Monto Irregular
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <UTabs :items="items" class="w-full" color="neutral">
      <template #ayuntamientos>
        <GraphicsDrawPolarArea
          :data="montoIrregular.ayuntamientos"
          title="Monto Irregular en Ayuntamientos"
          dataSet="monto"
        />
        <drawTable
          :data="montoIrregular.ayuntamientos"
          :columns="columns"
          title="Monto Irregular en Ayuntamientos"
          class="mt-5"
        />
      </template>
      <template #poderes>
        <GraphicsDrawPolarArea
          :data="montoIrregular.poderes"
          title="Monto Irregular en Poderes del Estado"
          dataSet="monto"
        />
        <drawTable
          :data="montoIrregular.poderes"
          :columns="columns"
          title="Monto Irregular en Poderes del Estado"
          class="mt-5"
        />
      </template>
      <template #dif>
        <GraphicsDrawPolarArea
          :data="montoIrregular.dif"
          title="Monto Irregular en DIF"
          dataSet="monto"
        />
        <drawTable
          :data="montoIrregular.dif"
          :columns="columns"
          title="Monto Irregular en DIF"
          class="mt-5"
        />
      </template>
      <template #aguas>
        <GraphicsDrawPolarArea
          :data="montoIrregular.aguas"
          title="Monto Irregular en Sistemas de Agua"
          dataSet="monto"
        />
        <drawTable
          :data="montoIrregular.aguas"
          :columns="columns"
          title="Monto Irregular en Sistemas de Agua"
          class="mt-5"
        />
      </template>
    </UTabs>
  </div>
</template>

<script setup>
import montoIrregular from "@/data/montoIrregular.json";
import GraphicsDrawPolarArea from "@/components/graphics/drawPolarArea.vue";
import drawTable from "@/components/drawTable.vue";
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Monto Irregular",
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
    accessorKey: "monoto",
    header: "Monto",
    meta: {
      class: {
        th: "text-center",
        td: "text-right font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("monoto"));
      return new Intl.NumberFormat("es-MX", {
        style: "currency",
        currency: "MXN",
      }).format(amount);
    },
  },
];
</script>

<style scoped></style>
