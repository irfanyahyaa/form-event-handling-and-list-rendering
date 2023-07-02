<script>
import "bootstrap/dist/css/bootstrap.css";
import "bootstrap-vue/dist/bootstrap-vue.css";
import Form from "./components/Form.vue";

export default {
  components: {
    Form,
  },
  methods: {
    handleAddTask(value) {
      console.log(value);
    },
  },
};
</script>

<template>
  <div>
    <Form title="Form Penilaian Siswa" @add-task="handleAddTask"/>
  </div>
</template>
