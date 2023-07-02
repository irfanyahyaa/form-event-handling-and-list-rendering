<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
      default: "Form Penilaian Siswa",
    },
    lists: [],
  },
  emits: ['addTask'],
  data() {
    return {
      form: {
        nis: "",
        nama: "",
        nilai: "",
      },
    };
  },
  methods: {
    addTask() {
      console.log("title: ", this.titleValue);
      console.log("description: ", this.descriptionValue);
      this.lists.push({
        id: this.lists.length + 1,
        title: this.titleValue,
        description: this.descriptionValue,
        isDone: false,
      });
      this.$emit("addTask", this.lists);
    },
    // deleteTask(task) {
    //   const index = this.lists.indexOf(task);
    //   if (index !== -1) {
    //     this.lists.splice(index, 1);
    //   }
    // },
    saveTask() {
      this.addTask();
      this.clearForm();
    },
    cancelTask() {
      this.clearForm();
    },
    clearForm() {
      this.titleValue = "";
      this.descriptionValue = "";
      this.isCreating = false;
    },
  },
};
</script>

<template>
  <div class="m-5">
    <h1>{{ title }}</h1>
    <section class="form">
      <div class="field mb-2">
        <label class="label">No Induk Siswa</label>
        <div class="control">
          <input
            v-model="form.nis"
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
            v-model="form.nama"
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
            v-model="form.nilai"
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
    <!-- <section class="content">
      <ul>
        <li v-for="(item, k) in form">
          <strong>{{ k }}:</strong> {{ item }}
        </li>
      </ul>
    </section> -->
  </div>
</template>

<style></style>
