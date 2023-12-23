<template>
  <div class="flex sm:flex-row flex-col w-full gap-2">
    <div class="flex flex-col sm:w-1/2 w-full justify-start">
      <h1 class="font-bold">TO-DO</h1>
      <div v-for="(item, index) in items" :key="index">
        <div
          v-if="item.status === false"
          class="flex flex-col justify-between border border-gray-600 p-4 rounded my-1 h-[90px]"
        >
          <h1 class="text-lg font-semibold">{{ item.name }}</h1>
          <div class="flex justify-between">
            <div class="flex gap-1 items-center">
              <div
                class="w-[15px] h-[15px] rounded"
                :class="{
                  'bg-blue-500': item.priority === 'Low',
                  'bg-red-500': item.priority === 'High',
                  'bg-yellow-500': item.priority === 'Medium',
                }"
              ></div>
              {{ item.priority }}
            </div>
            <div class="flex gap-2">
              <button
                @click="deleteItems(index)"
                class="bg-red-600 text-white rounded-xl py-1 px-3 shadow-sm"
              >
                Hapus
              </button>
              <button
                @click="toggleStatus(index)"
                class="bg-green-600 text-white rounded-xl py-1 px-3 shadow-sm"
              >
                Selesai
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="flex flex-col sm:w-1/2">
      <h1 class="font-bold">DONE</h1>
      <div v-for="(item, index) in items" :key="index">
        <div
          v-if="item.status == true"
          class="flex flex-col justify-between border border-gray-500 p-4 rounded my-1 h-[90px]"
        >
          <h1 class="text-lg font-semibold">{{ item.name }}</h1>
          <div class="flex justify-between">
            <div class="flex gap-1 items-center">
              <div
                class="w-[15px] h-[15px] rounded"
                :class="{
                  'bg-blue-500': item.priority === 'Low',
                  'bg-red-500': item.priority === 'High',
                  'bg-yellow-500': item.priority === 'Medium',
                }"
              ></div>
              {{ item.priority }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    items: {
      type: Array,
      required: true,
    },
    changeAttribute: Function,
    index: Number,
  },
  methods: {
    toggleStatus(index) {
      this.$emit("toggle-status", index);
    },
    deleteItems(index) {
      this.$emit("delete-items", index);
    },
  },
};
</script>
