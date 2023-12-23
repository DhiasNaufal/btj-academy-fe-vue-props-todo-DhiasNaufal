<template>
  <div class="border border-gray-500 rounded p-3 w-full sm:px-11">
    <form id="form" @submit.prevent="addItems" class="sm:flex gap-5 items-end">
      <div class="flex flex-col sm:w-1/2">
        <label for="nama">Nama</label>
        <input
          type="text"
          name="nama"
          id="nama"
          v-model="newItem.name"
          class="border border-gray-500 h-[40px] p-1"
        />
      </div>
      <div class="flex flex-col sm:w-1/2">
        <label for="priority">Priority</label>
        <select
          name="priority"
          id="priority"
          v-model="newItem.priority"
          class="border border-gray-500 h-[40px] p-1"
        >
          <option v-for="(item, index) in priorityList" :value="item">
            {{ item }}
          </option>
        </select>
      </div>
      <button
        type="submit"
        class="bg-green-600 text-white px-2 flex h-[40px] items-center rounded-lg shadow-sm w-full sm:w-[100px] justify-center mt-2"
      >
        Tambah
      </button>
    </form>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newItem: {
        name: null,
        priority: null,
        status: false,
      },
      priorityList: ["Low", "Medium", "High"],
    };
  },
  methods: {
    addItems() {
      this.$emit("add-items", this.newItem);
      this.name = null;
      this.priority = null;
    },
  },
};
</script>
