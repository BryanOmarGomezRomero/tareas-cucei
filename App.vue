<template>
  <div class="app">
    <h1>📘 Tareas CUCEI</h1>

    <!-- Formulario para nueva tarea -->
    <div class="formulario">
      <input v-model="nuevaTarea.nombre" placeholder="Nombre de la tarea" />
      <input type="date" v-model="nuevaTarea.fecha" />
      <input v-model="nuevaTarea.materia" placeholder="Materia" />

      <select v-model="nuevaTarea.dificultad">
        <option value="Fácil">Fácil</option>
        <option value="Medio">Medio</option>
        <option value="Difícil">Difícil</option>
      </select>

      <input type="number" v-model="nuevaTarea.tiempo" placeholder="Horas estimadas" min="1" />

      <button @click="agregarTarea">➕ Agregar</button>
    </div>

    <!-- Lista de tareas -->
    <ul>
      <TareaItem
        v-for="(tarea, index) in tareas"
        :key="index"
        :tarea="tarea"
        @eliminar="eliminarTarea(index)"
      />
    </ul>
  </div>
</template>

<script>
import TareaItem from "./components/TareaItem.vue"

export default {
  components: { TareaItem },
  data() {
    return {
      nuevaTarea: {
        nombre: "",
        fecha: "",
        materia: "",
        dificultad: "Fácil",
        tiempo: ""
      },
      tareas: []
    }
  },
  methods: {
    agregarTarea() {
      if (this.nuevaTarea.nombre.trim() !== "") {
        this.tareas.push({ ...this.nuevaTarea })
        this.nuevaTarea = { nombre: "", fecha: "", materia: "", dificultad: "Fácil", tiempo: "" }
      }
    },
    eliminarTarea(index) {
      this.tareas.splice(index, 1)
    }
  }
}
</script>

<style>
.app {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 20px;
}

.formulario {
  margin-bottom: 20px;
}

input, select {
  margin: 5px;
  padding: 5px;
}

button {
  margin: 5px;
  padding: 5px 10px;
  cursor: pointer;
}

ul {
  list-style: none;
  padding: 0;
}
</style>


