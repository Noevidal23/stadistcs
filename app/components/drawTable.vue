<template>
  <div class="flex flex-col gap-2 border-2 border-gray-200 rounded">
    <h1 class="text-xl font-bold text-center mt-2">{{ title }}</h1>
    <UTable :data="data" :columns="columns" />
  </div>
</template>

<script setup>
const props = defineProps(["data", "columns", "title"]);
</script>

<style scoped></style>
