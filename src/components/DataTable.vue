<script setup>
import { computed, defineProps, ref } from 'vue'
import SearchForm from './SearchForm.vue'
import FilterDropdown from './FilterDropdown.vue'
import FilterRadios from './FilterRadios.vue'

const searchFilter = ref('')
const radioFilter = ref('')
const props = defineProps({
  items: {
    type: Array,
    required: true
  }
})

const filteredItems = computed(() => {
  if (searchFilter)
    return props.items.filter((item) =>
      item.todo.toLowerCase().includes(searchFilter.value.toLowerCase())
    )
  return props.items
})

const handleSearch = (search) => {
  searchFilter.value = search
}

const handleRadioFilter = (filter) => {
  radioFilter.value = filter
}
</script>

<template>
  <div class="bg-white relative border rounded-lg">
    <div class="flex items-center justify-between">
      <SearchForm @search="handleSearch" />

      <div class="flex items-center justify-end text-sm font-semibold">
        <FilterRadios @filter="handleRadioFilter" />
        <FilterDropdown />
      </div>
    </div>
    <table class="w-full text-sm text-left text-gray-500">
      <thead class="text-xs text-gray-700 uppercase bg-gray-50">
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
        <tr v-for="item in filteredItems" :key="item.id" class="border-b">
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
