<script setup>
import { ref, defineProps, computed } from 'vue'

const emit = defineEmits(['filter'])
const show = ref(false)
const props = defineProps({
  items: {
    type: Array,
    required: true
  }
})

const statuses = computed(() => {
  const statusSet = new Set(props.items.map((item) => item.status))
  return Array.from(statusSet)
})

const filter = (e) => {
  emit('filter', e.target.value)
}
</script>

<template>
  <div class="relative flex items-center w-full px-4">
    <button
      @click="show = !show"
      class="bg-white w-full flex items-center justify-center py-2 px-4 text-sm font-medium text-gray-900 border rounded-lg hover:bg-gray-50 hover:text-indigo-500"
    >
      Filter
    </button>

    <div v-if="show" class="absolute top-12 right-0 z-10 w-48 p-3 bg-white rounded-lg shadow">
      <h6 class="mb-3 text-sm font-medium text-gray-900">Status</h6>
      <ul class="space-y-2 text-sm">
        <li v-for="(status, index) in statuses" class="flex items-center">
          <input
            @change="filter"
            :id="`filter_option_${index}`"
            type="checkbox"
            :value="status"
            class="w-4 h-4 bg-gray-100 border-gray-300 rounded"
          />
          <label :for="`filter_option_${index}`" class="ml-2 text-sm font-medium text-gray-900">{{
            status
          }}</label>
        </li>
      </ul>
    </div>
  </div>
</template>
