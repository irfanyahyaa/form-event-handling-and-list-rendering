<script>
export default {
  props: {
    lists: Object,
  },
};
</script>

<template>
  <div>
    <div
      v-for="list of lists"
      class="item-task d-flex align-items-start border-bottom pt-3 pb-4"
      :key="list.id"
    >
      <div class="d-flex flex-column">
        <div :class="('title-task mb-2', list.isDone ? 'completed-task' : '')">
          No. Induk Siswa: {{ list.nis }}
        </div>
        <div class="description-task small text-muted">
          Nama: {{ list.nama }}
        </div>
        <div class="description-task small text-muted">
          Nilai: <strong>{{ list.nilai }}</strong>
        </div>
        <a href="#" @click="deleteTask(list)">Delete</a>
      </div>
    </div>
  </div>
</template>
