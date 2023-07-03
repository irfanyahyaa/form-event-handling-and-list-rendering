<script>
import List from "./List.vue";

export default {
  components: {
    List,
  },
  props: {
    title: {
      type: String,
      required: true,
      default: "Form Penilaian Siswa",
    },
  },
  emits: ["addTask"],
  data() {
    return {
      lists: [],
      nisValue: "",
      namaValue: "",
      nilaiValue: "",
    };
  },
  // computed: {
  //   average() {
  //     return this.lists.reduce((total, curr) => (total = total + curr.nilai), 0) / lists.length
  //   }
  // },
  methods: {
    addTask() {
      console.log("nis: ", this.nisValue);
      console.log("nama: ", this.namaValue);
      console.log("nilai: ", this.nilaiValue);
      this.lists.push({
        id: this.lists.length + 1,
        nis: this.nisValue,
        nama: this.namaValue,
        nilai: this.nilaiValue,
        isDone: false,
      });
      this.$emit("addTask", this.lists);
    },
    deleteTask(list) {
      const index = this.lists.indexOf(list);
      if (index !== -1) {
        this.lists.splice(index, 1);
      }
    },
    saveTask() {
      this.addTask();
      this.clearForm();
    },
    cancelTask() {
      this.clearForm();
    },
    clearForm() {
      this.nisValue = "";
      this.namaValue = "";
      this.nilaiValue = "";
    },
  },
};
</script>

<template>
  <div class="m-5">
    <h1>{{ title }}</h1>
    <section class="form border-bottom pt-2 pb-4">
      <div class="field mb-2">
        <label class="label">No Induk Siswa</label>
        <div class="control">
          <input
            v-model="nisValue"
            class="form-control"
            type="number"
            placeholder="Masukkan NIS"
          />
        </div>
      </div>
      <div class="field mb-2">
        <label class="label">Nama Siswa</label>
        <div class="control">
          <input
            v-model="namaValue"
            class="form-control"
            type="text"
            placeholder="Masukkan Nama"
          />
        </div>
      </div>
      <div class="field mb-2">
        <label class="label">Nilai Tugas</label>
        <div class="control">
          <input
            v-model="nilaiValue"
            class="form-control"
            type="number"
            min="0"
            max="100"
            placeholder="Masukkan Nilai"
          />
        </div>
      </div>
      <div class="button-wrapper d-flex">
        <button class="btn btn-primary me-2" @click="saveTask">Save</button>
        <button class="btn btn-outline-secondary" @click="clearForm">
          Cancel
        </button>
      </div>
    </section>
    <List :lists="lists" />
    <div class="average-list mt-3" v-if="lists.length">
      <p>
        Rata-rata niai dari <strong>{{ lists.length }}</strong> orang siswa
        adalah:
        <strong>{{
          lists.reduce((total, curr) => (total = total + curr.nilai), 0) /
          lists.length
        }}</strong>
      </p>
    </div>
  </div>
</template>

<style></style>
