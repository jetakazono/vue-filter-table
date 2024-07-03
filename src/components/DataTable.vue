<script setup>
import { defineProps } from 'vue'

const props = defineProps({
  items: {
    type: Array,
    required: true
  }
})
</script>

<template>
  <div class="bg-white relative border rounded-lg">
    <table class="w-full text-sm text-left text-gray-500">
      <thead class="text-xs text-gray-700 uppercase bg-gray-300">
        <tr>
          <th class="px-4 py-3">ID</th>
          <th class="px-4 py-3">Assigned To</th>
          <th class="px-4 py-3">Status</th>
          <!-- <th class="px-4 py-3">Title</th> -->
          <!-- <th class="px-4 py-3">Due At</th> -->
          <th class="px-4 py-3"><span class="sr-only">Actions</span></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id" class="border-b">
          <td class="px-4 py-3 font-medium text-gray-900">{{ item.id }}</td>
          <td class="px-4 py-3 font-medium text-gray-900">{{ item.todo }}</td>
          <td class="px-4 py-3">{{ item.completed }}</td>
          <td class="px-4 py-3 flex items-center justify-end">
            <a class="text-indigo-500 hover:underline" href="#">Details</a>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style scoped></style>

const props = defineProps({ items: { type: Array, required: true } })
