<template>
  <div>
    <div>N° ID Tarea:
      <select v-model="idu" @change="cambiarDescripcionT">
        <option v-for="opcion in BaseS" :key="opcion.id" :value="opcion.id">
          {{ opcion.id + "-" + opcion.descripcion}}
        </option>
      </select>
    </div>
    <table>
      <thead>
        <tr>
          <th>ID asignación</th>
          <th>ID usuario</th>
          <th>Nombre</th>
          <th>Apellido</th>
          <th>Tarea</th>
          <th>Estado</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="opcion in BaseE" :key="opcion.id">
          <td>{{ opcion.id }}</td>
          <td>{{ opcion.Usuario.id }}</td>
          <td>{{ opcion.Usuario.nombre }}</td>
          <td>{{ opcion.Usuario.apellido }}</td>
          <td>{{ opcion.Tarea.descripcion }}</td>
          <td>{{ opcion.Estado.descripcion }}</td>
          
        </tr>
      </tbody>
    </table>
    <SinRegistros v-if="sreg"></SinRegistros>
  </div>
</template>

<style scoped>
  form {
    color: black;
    background-color: rgb(75, 82, 148);
    border-style: solid;
    border-color: blue;
  }
  h3 {
    color: white;
    background-color: rgb(1, 1, 26);
  }
  table {
    font-size: 14px;
    width: 100px;
    margin: 0 auto;
    text-align: center;
    border-style: solid;
    border-color: black;
    background-color: white;
  }
  th {
    color: white;
    background-color: black;
    border-style: solid;
    border-color: black;
    align-items: center;
  }
  td {
    border-style: solid;
    border-color: black;
    align-items: center;
  }
</style>

<script setup>
import { ref, onMounted } from 'vue';
import SinRegistros from "../components/Sin registros.vue"

const Base = ref([]);
const BaseE = ref([]);
const BaseS = ref([]);
const BaseF = ref([]);
const idu = ref('');
const sreg = ref(false);

onMounted(async () => {
  const options = {
    method: 'GET',
    headers: {
      'Content-Type': 'application/json'
    }
  };
  const responseAsignacion = await fetch('http://localhost:3000/asignar', options);
  Base.value = await responseAsignacion.json();
  const responseAsignacionS = await fetch('http://localhost:3000/tareas', options);
  BaseS.value = await responseAsignacionS.json();
  BaseE.value = Base.value;
});

const cambiarDescripcionT = async () => {
  const options = {
    method: 'GET',
    headers: {
      'Content-Type': 'application/json'
    }
  };
  const responseAsignacion = await fetch(`http://localhost:3000/asignar/tareas/` + idu.value, options);
  BaseE.value = await responseAsignacion.json();
     if(BaseE.value.length === 0){
         sreg.value = true;
     }else{sreg.value = false}
  
  };

</script>