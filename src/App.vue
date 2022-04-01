<template>
  <div id="app">
    <form>
      <div class="mb-3">
        <h1>Nueva Tarea</h1>
        <label class="me-3">Tarea</label>
        <input
          type="text"
          v-model="task"
          class="form-control w-50 d-inline"
          placeholder="Ingresa nueva tarea"
        />
      </div>
      <button type="button" @click="showTask" class="btn btn-primary">
        Añadir
      </button>
    </form>
    <ListTask :addTask="newTask" @delete-task="deleteTask"></ListTask>
  </div>
</template>

<script>
import ListTask from "@/components/ListTask.vue";

export default {
  name: "App",
  data() {
    return {
      newTask: [],
      show: true,
      task: "",
    };
  },
  components: {
    ListTask,
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
    deleteTask(indice) {
      this.newTask.splice(indice, 1);
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
