<script setup>
import { ref } from 'vue'
import { data } from './data.ts'
import DataTable from './components/DataTable.vue'

const items = ref(data)

// onMounted(async () => {
//   const response = await fetch('')
//   items.value = await response.json()
// })
</script>

<template>
  <div class="p-8 bg-gray-50 min-h-screen">
    <DataTable :items="items" />
  </div>
</template>

<style scoped></style>
