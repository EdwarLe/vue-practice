<template>
  <div>
    <h1>TO DO</h1>
    <form v-on:submit.prevent="createTask">
      <input type="text" v-model="tasks.name" />
      <input type="submit" value="Agregar Tarea" />
    </form>
    <table>
      <thead>
        <tr>
          <th>Hecho</th>
          <th>Nombre</th>
          <th>Eliminar</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="task in tasks">
          <td>
            <input type="checkbox" v-model="task.done" />
          </td>
          <td>{{ task.name }}</td>
          <td>
            <button v-on:click="deleteUser(task)">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {
          name: "Correr",
          done: false,
        },
        {
          name: "Estudiar",
          done: true,
        },
        {
          name: "Cocinar",
          done: false,
        },
      ],
    };
  },
  methods: {
    deleteUser(task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    },
    createTask(e) {
      this.tasks.push({
        name: this.tasks.name,
        done: false,
      });
      this.tasks.name = "";
    },
  },
};
</script>

<style></style>
