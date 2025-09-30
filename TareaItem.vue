<template>
  <li class="tarea">
    <h3>{{ tarea.nombre }}</h3>
    <p>📅 Fecha de entrega: {{ tarea.fecha }}</p>
    <p>📚 Materia: {{ tarea.materia }}</p>
    <p>🎚️ Dificultad: <strong>{{ tarea.dificultad }}</strong></p>
    <p>⏳ Tiempo estimado: {{ tarea.tiempo }} horas</p>
    <button @click="$emit('eliminar')">❌ Eliminar</button>
  </li>
</template>

<script>
export default {
  props: ["tarea"]
}
</script>

<style>
.tarea {
  border: 1px solid #ccc;
  border-radius: 8px;
  padding: 10px;
  margin: 10px auto;
  width: 300px;
  text-align: left;
}

.tarea h3 {
  margin: 0;
}

button {
  margin-top: 10px;
  background: red;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
  border-radius: 5px;
}
</style>
