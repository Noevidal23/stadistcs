<template>
  <USeparator class="my-3" />
  <h1 class="text-xl font-bold text-center my-2">{{ title }}</h1>
  <UTabs :items="items" class="w-full" color="error">
    <template #ingresos>
      <drawTable :data="data.ingreso" :columns="columns" title="Ingresos" />
    </template>
    <template #egresos>
      <drawTable :data="data.egreso" :columns="columns" title="Egresos" />
    </template>
    <template #estadoSituacionFinanciera>
      <drawTable
        :data="data.situacionFinanciera"
        :columns="columns"
        title="Estado Situación Financiera"
      />
    </template>
    <template #disponibilidadPresupuestal>
      <drawTable
        :data="data.disponibilidad"
        :columns="columns"
        title="Disponibilidad Presupuestal"
      />
    </template>
  </UTabs>
</template>

<script setup>
const props = defineProps(["data", "title"]);

const items = [
  {
    label: "Ingresos",
    icon: "i-lucide-banknote-arrow-up",
    slot: "ingresos",
  },
  {
    label: "Egresos",
    icon: "i-lucide-banknote-arrow-down",
    slot: "egresos",
  },
  {
    label: "Financiera",
    icon: "i-lucide-circle-dollar-sign",
    slot: "estadoSituacionFinanciera",
  },
  {
    label: "Presupuestal",
    icon: "i-lucide-wallet",
    slot: "disponibilidadPresupuestal",
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
    accessorKey: "UNIVERSO",
    header: "Universo",
    meta: {
      class: {
        th: "text-center",
        td: "text-right font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("UNIVERSO"));
      return new Intl.NumberFormat("es-MX", {
        style: "currency",
        currency: "MXN",
      }).format(amount);
    },
  },
  {
    accessorKey: "MUESTRA",
    header: "Muestra",
    meta: {
      class: {
        th: "text-center",
        td: "text-right font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("MUESTRA"));
      return new Intl.NumberFormat("es-MX", {
        style: "currency",
        currency: "MXN",
      }).format(amount);
    },
  },
  {
    accessorKey: "PORCENTAJE",
    header: "%",
    meta: {
      class: {
        th: "text-center",
        td: "text-right font-medium",
      },
    },
    cell: ({ row }) => {
      const amount = Number.parseFloat(row.getValue("PORCENTAJE"));
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
