<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Seguimiento a Resultados
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <UTabs :items="items" class="w-full" color="neutral">
      <template #ayuntamientos>
        <drawTable
          :data="seguimiento.municipios"
          :columns="columns"
          title="Ayuntamientos"
        />
      </template>
      <template #poderes>
        <drawTable
          :data="seguimiento.poderes"
          :columns="columns"
          title="Poderes y Entes Públicos"
        />
      </template>
      <template #dif>
        <drawTable
          :data="seguimiento.dif"
          :columns="columns"
          title="DIF "
        />
      </template>
      <template #aguas>
        <drawTable
          :data="seguimiento.agua"
          :columns="columns"
          title="Sistemas de Agua Potable"
        />
      </template>
    </UTabs>
  </div>
</template>

<script setup>
import seguimiento from "@/data/seguimiento.json";
import drawTable from "~/components/drawTable.vue";
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Seguimiento a Resultados",
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
    accessorKey: "ejercicio",
    header: "Ejercicio",
    meta: {
      class: {
        th: "text-center",
        td: "text-center font-medium",
      },
    },
  },
  {
    accessorKey: "observado",
    header: "Monto Observado",
    meta: {
      class: {
        th: "text-center",
        td: "text-right font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("observado"));
      return new Intl.NumberFormat("es-MX", {
        style: "currency",
        currency: "MXN",
      }).format(amount);
    },
  },
  {
    accessorKey: "solventado",
    header: "Monto Solventado",
    meta: {
      class: {
        th: "text-center",
        td: "text-right font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("solventado"));
      return new Intl.NumberFormat("es-MX", {
        style: "currency",
        currency: "MXN",
      }).format(amount);
    },
  },
  {
    accessorKey: "persistente",
    header: "Monto Persistente",
    meta: {
      class: {
        th: "text-center",
        td: "text-right font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("persistente"));
      return new Intl.NumberFormat("es-MX", {
        style: "currency",
        currency: "MXN",
      }).format(amount);
    },
  },
];
</script>

<style scoped></style>
