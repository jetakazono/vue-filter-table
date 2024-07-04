<script setup>
import { onMounted, ref } from 'vue'
import DataTable from './components/DataTable.vue'

const items = ref([])

onMounted(async () => {
  const response = await fetch('https://dummyjson.com/todos')
  const data = await response.json()
  items.value = data.todos
})
</script>

<template>
  <div class="p-8 bg-gray-50 min-h-screen">
    <DataTable :items="items" />
  </div>
</template>

<style scoped></style>
