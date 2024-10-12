<script setup>
 import Alta  from './components/Alta.vue'
 import Baja from './components/Baja.vue'
 import Modi from './components/Modi.vue'
 import { ref } from 'vue';
 const alta2 = ref(false);
 const baja = ref(false);
 const modi = ref(false);

  const TareaAlta = () => {
       
       alta2.value = true;
       baja.value = false;
       modi.value = false;
           
  }

  const TareaBaja = () => {
       
       alta2.value = false;
       baja.value = true;
       modi.value = false;
           
  } 


  const TareaModi = () => {
       
       modi.value = true;
       alta2.value = false;
       baja.value = false;
       
       
           
  }

  
  
  const Seguimiento = () => {
       alert("En construccion")
  }


  const Salir = () => {
    alert("En construccion")
       
  }

  
   
</script>

<style>
  h1{
    color: white;
    background-color: black;
    text-align: center;
  }
  h3{
    color:grey
  }
  li{
    color:black
  }

  #div1{
    border-color: black;
    border-style: solid;
  }
</style>

<template>
  
  <h1>Gestión de Tareas:</h1>
  <br><br><br>
  <h2>Menu principal:</h2>
  <br><br>
  <div>
    <ul>
      <div id="div1">
        <li>Tareas: </li> 
         Alta:<input type="radio" name="opcion" @click="TareaAlta()" >   
         Baja:<input type="radio" name="opcion" @click="TareaBaja()">
         Modificar:<input type="radio" name="opcion" @click="TareaModi()">
      </div>
      <br>
      <li>Seguimiento <button @click="Seguimiento()">-></button></li>
      <li>Salir <button @click="Salir()">-></button></li>
    </ul>
  </div>
  <br><br><br>
  <Alta v-show="alta2"></Alta>
  <Baja v-show="baja"></Baja>
  <Modi v-show="modi"></Modi>
</template>
