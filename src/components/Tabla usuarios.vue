<template>
    
    <table>
      <thead>
        <tr>
          <th>ID usuario</th>
          <th>Nombre</th>
          <th>Apellido</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="opcion in Base" :key="opcion.id">
          <td>{{ opcion.id }}</td>
          <td>{{ opcion.nombre }}</td>
          <td>{{ opcion.apellido }}</td>
        </tr>
      </tbody>
    </table>
    <SinUsuarios v-if="sreg"></SinUsuarios>
    <br>

</template>

<style scoped>
   
   form {
    color: black;
    background-color: rgb(75, 82, 148);
    border-style: solid;
    border-color: blue
   }
   h3{
    color: white;
    background-color: rgb(1, 1, 26);
   }
   table{ 
    font-size: 9px; 
    text-align: center;  
    border-style: solid;
    border-color: black;
    border-color: black;
    background-color: white;
   }
   th{
    color: white;
    background-color: black;  
    border-style: solid;  
    border-color: black;
    border-color: black;
    align-items: center;
   }
   td{
    border-style: solid;  
    border-color: black;
    border-color: black;
    align-items: center;
   }
</style>

<script setup>
   import { ref, onMounted } from 'vue';
   import SinUsuarios from "../components/Sin usuarios.vue"
   const Base = ref([]);
   const sreg = ref(false)
   

   onMounted(async () => {
    const options = {
        method: 'GET',
        headers: {
            'Content-Type': 'application/json'
        }
    };
    const responseAsignacion = await fetch('http://localhost:3000/usuarios', options);
    Base.value = await responseAsignacion.json();
       if(Base.value.length === 0){
           sreg.value = true;
       }else{sreg.value = false}
   });  
</script>