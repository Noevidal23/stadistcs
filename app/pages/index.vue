<template>
  <UModal
    title="ESTADÍSTICAS DE LOS INFORMES CUENTAS PÚBLICAS"
    description="2017 - 2024"
    v-model:open="open"
  >
    <template #body>
      <p class="text-justify">
        La Auditoría Superior del Estado ha auditado diversos entes durante las
        revisiones de las Cuentas Públicas de 2017 a 2024. Estos entes incluyen
        Poderes del Estado, Organismos Autónomos, Ayuntamientos, Sistemas
        Municipales de Agua Potable y Alcantarillado y Sistemas para el
        Desarrollo Integral de la Familia (DIF) Municipales.
      </p>
    </template>
  </UModal>
  <div class="flex flex-col gap-4 items-center h-dvh mt-3 px-4">
    <img src="/logo.png" alt="Logotipo ASE" class="w-32" />
    <h1 class="text-xl font-bold text-center pt-2">
      ESTADÍSTICAS DE LOS INFORMES CUENTAS PÚBLICAS
    </h1>
    <ul class="flex flex-col gap-3">
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/entes-auditados')"
      >
        Número de Entes Auditados
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/numero-auditorias')"
      >
        Número de Auditorías
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/muestra')"
      >
        Muestras
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/observaciones')"
      >
        Número de Observaciones
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/monto')"
      >
        Monto Irregular
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/acciones')"
      >
        Acciones y Recomendaciones
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/supuestos')"
      >
        Observaciones por Supuestos
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/revision-federal')"
      >
        Revisión a los Recursos Federales
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/tipo-informe')"
      >
        Tipo de Informes
      </li>
      <li
        class="text-center text-lg py-1 rounded-lg bg-red-800 text-white cursor-pointer"
        @click="navigateTo('/resumen')"
      >
        Resumen de los Informes Entregados (2017 - 2024)
      </li>
    </ul>
  </div>
</template>

<script setup>
const open = ref(false);
</script>

<style scoped></style>
