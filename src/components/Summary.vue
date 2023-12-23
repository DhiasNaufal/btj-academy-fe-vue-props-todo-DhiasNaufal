<template>
  <h1 class="text-left">TODO APP - Array of Objects</h1>
  <div class="sm:flex gap-3 w-full items-start text-start hidden xxl:flex">
    <div
      v-for="priority in bambang"
      :key="priority.title"
      class="border border-gray-500 rounded p-3 flex flex-col"
    >
      <h1 class="text-center">
        {{ priority.title }}
      </h1>
      <p class="text-center">{{ priority.value }}</p>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    bambang: {
      type: Array,
      required: true,
    },
  },
};
</script>
