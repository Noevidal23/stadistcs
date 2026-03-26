<template>
  <div class="flex flex-col gap-4 mt-5 w-full md:w-2/3">
    <h1
      class="text-2xl font-bold text-center text-white bg-red-800 py-2 mt-2 rounded-br-2xl rounded-tl-2xl"
    >
      Muestra
    </h1>
    <UBreadcrumb :items="itemsBreadcrumb" />
    <UTabs :items="items" class="w-full" color="neutral">
      <template #ayuntamientos>
        <drawInternalTabs :data="muestra.ayuntamiento" title="Ayuntamientos" />
        <drawLine :data="muestra.ayuntamiento" title="Muestra Ayuntamientos" />
      </template>
      <template #poderes>
        <drawInternalTabs :data="muestra.poderes" title="Poderes del Estado" />
        <drawLine :data="muestra.poderes" title="Muestra Poderes del Estado" />
      </template>
      <template #dif>
        <DrawInternalTabsShort :data="muestra.dif" title="DIF" />
        <drawLineShort :data="muestra.dif" title="Muestra DIF" />
      </template>
      <template #aguas>
        <DrawInternalTabsShort :data="muestra.aguas" title="Sistemas de Agua" />
        <drawLineShort :data="muestra.aguas" title="Muestra Sistemas de Agua" />
      </template>
    </UTabs>
  </div>
</template>

<script setup>
import drawInternalTabs from "@/components/drawInternalTabs.vue";
import drawLine from "@/components/graphics/drawLine.vue";
import drawLineShort from "@/components/graphics/drawLineShort.vue";
import muestra from "@/data/muestra.json";
const itemsBreadcrumb = [
  {
    label: "Inicio",
    to: "/",
  },
  {
    label: "Muestra",
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
</script>

<style scoped></style>
