<script setup>
const emit = defineEmits(['search'])

const search = (e) => {
  emit('search', e.target.value)
}
</script>

<template>
  <form class="py-3 px-4 flex items-center">
    <label for="sr-only"></label>
    <div class="relative w-full">
      <input
        @input="search"
        type="text"
        name="Search"
        id="Search"
        placeholder="Search"
        class="bg-gray-50 text-gray-900 py-1 px-2 rounded-md border border-gray-300"
      />
    </div>
  </form>
</template>
