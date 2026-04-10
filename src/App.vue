<template>
  <div class="container">
    <h1>Formulario de Registro</h1>

    <form @submit.prevent="agregarRegistro">
    
      <input v-model="form.nombre" placeholder="Nombre" required />
      <input v-model="form.apellido" placeholder="Apellido" required />

      <div>
        <label>
          <input type="radio" value="Masculino" v-model="form.genero" />
          Masculino
        </label>
        <label>
          <input type="radio" value="Femenino" v-model="form.genero" />
          Femenino
        </label>
      </div>

      <select v-model="form.carrera" required>
        <option disabled value="">Seleccione una carrera</option>
        <option>Ingeniería</option>
        <option>Medicina</option>
        <option>Derecho</option>
      </select>

      <button type="submit" class="btn">Agregar</button>
    </form>

    <h2>Registros</h2>

    <table border="1">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Apellido</th>
          <th>Género</th>
          <th>Carrera</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(item, index) in registros" :key="index">
          <td>{{ item.nombre }}</td>
          <td>{{ item.apellido }}</td>
          <td>{{ item.genero }}</td>
          <td>{{ item.carrera }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
import { reactive, ref } from 'vue'

const form = reactive({
  nombre: '',
  apellido: '',
  genero: '',
  carrera: ''
})

const registros = ref([])

function agregarRegistro() {
  registros.value.push({ ...form })

  // Limpiar formulario
  form.nombre = ''
  form.apellido = ''
  form.genero = ''
  form.carrera = ''
}
</script>

