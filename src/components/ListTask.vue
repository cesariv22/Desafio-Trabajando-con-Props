<template>
  <div>
    <h2 class="mt-2">Listado de Tareas</h2>
    <ul v-if="addTask.length > 0" class="list-group list-group-">
      <li
        v-for="(objTask, i) of addTask"
        :key="+i"
        class="list-group-item list-task mx-5"
      >
        {{ objTask }}
        <button
          @click="btnDeleteTask(i)"
          class="btn-danger rounded button-delete"
        >
          Eliminar
        </button>
      </li>
    </ul>
    <ul v-else class="fs-3">
      Sin tareas aún
    </ul>
  </div>
</template>

<script>
export default {
  name: "ListTask",
  props: {
    addTask: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    showTask() {
      if (this.task == false) {
        alert("Ingresar una tarea");
      } else {
        this.newTask.push(this.task);
        return (this.task = "");
      }
    },
    btnDeleteTask(num) {
      this.$emit("delete-task", num);
    },
  },
};
</script>

<style>
.list-task {
  display: flex;
  justify-content: space-between;
}
</style>
