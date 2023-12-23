<template>
  <div class="sm:w-3/5 w-11/12 flex flex-col gap-5">
    <ringkasan :bambang="priorities" />
    <TaskForm @add-items="tambah"></TaskForm>
    <TaskItem
      :items="todoList"
      @toggle-status="selesai"
      @delete-items="hapus"
    ></TaskItem>
  </div>
</template>
<script>
import ringkasan from "./components/summary.vue";
import TaskForm from "./components/TaskForm.vue";
import TaskItem from "./components/TaskItem.vue";
export default {
  components: {
    ringkasan,
    TaskForm,
    TaskItem,
  },
  data() {
    return {
      todoList: [
        { id: 1, name: "Makan Nasi Rogeng", priority: "Medium", status: false },
        { id: 1, name: "Makan Nasi Rogeng", priority: "Low", status: false },
      ],
      sum: {},
      lol2: [],
    };
  },
  methods: {
    tambah(lol) {
      alert("kepencet");
      this.todoList.push(lol);
      return lol;
    },
    selesai(index) {
      this.todoList[index].status = true;
      // alert("tombol kepencet");
    },
    hapus(index) {
      this.todoList.splice(index, 1);
    },
  },
  computed: {
    totalPending() {
      return this.todoList.filter((item) => item.status === false).length;
      // return 8;
    },
    totalDone() {
      return this.todoList.filter((item) => item.status === true).length;
      // return 3;
    },
    totalLow() {
      return this.todoList.filter(
        (item) => item.status === false && item.priority === "Low"
      ).length;
      // return 0;
    },
    totalMed() {
      return this.todoList.filter(
        (item) => item.status === false && item.priority === "Medium"
      ).length;
      // return 0;
    },
    totalHigh() {
      return this.todoList.filter(
        (item) => item.status === false && item.priority === "High"
      ).length;
      // return 0;
    },
    priorities() {
      return [
        { title: "PENDING", value: this.totalPending },
        { title: "LOW PRIORITY", value: this.totalLow },
        { title: "MEDIUM PRIORITY", value: this.totalMed },
        { title: "HIGH PRIORITY", value: this.totalHigh },
        { title: "FINISHED", value: this.totalDone },
      ];
    },
  },
};
</script>
