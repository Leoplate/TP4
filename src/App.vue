<script setup>
 import Alta  from './components/Alta_Usuario_Tarea.vue'
 import Baja from './components/Baja_Usuario_Tarea.vue'
 import Modi from './components/Modi.vue'
 import GAlta from './components/GAlta.vue'
 import GBaja from './components/GBaja.vue'
 import GModi from './components/GModi.vue'
 import { ref } from 'vue';
 
 
 const alta2 = ref(false);
 const galta = ref(false);
 const gbaja = ref(false);
 const gmodi = ref(false);
 

 //const alta2 = false;
 const baja = ref(false);
 //const baja = false;
 const modi = ref(false);
//const modi = false;
  const TareaAlta = () => {
        
       alta2.value = true;
       baja.value = false;
       modi.value = false;
       galta.value = false;
       gbaja.value = false;
       gmodi.value = false;
  }

  const TareaBaja = () => {
       
       alta2.value = false;
       baja.value = true;
       modi.value = false;
       galta.value = false;
       gbaja.value = false;
       gmodi.value = false;    
  } 


  const TareaModi = () => {
       
       modi.value = true;
       alta2.value = false;
       baja.value = false;
       galta.value = false;
       gbaja.value = false;
       gmodi.value = false;     
  }

  const TareaGAlta = () => {
       
       modi.value = false;
       alta2.value = false;
       baja.value = false;
       galta.value = true;
       gbaja.value = false;
       gmodi.value = false;     
  } 
 
  const TareaGBaja = () => {
       
       modi.value = false;
       alta2.value = false;
       baja.value = false;
       galta.value = false;
       gbaja.value = true;
       gmodi.value = false;     
  } 
  
  const TareaGModi = () => {
       
       modi.value = false;
       alta2.value = false;
       baja.value = false;
       galta.value = false;
       gbaja.value = false;
       gmodi.value = true;     
  } 

  const Seguimiento = () => {
       alert("En construccion")
  }


  const Salir = () => {
    alert("En construccion")
    window.close();
       
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

  #div2{
    border-color: black;
    border-style: solid;
  }
</style>

<template>
  
  <h1>Gestión de Tareas:</h1>
  <h2>Menu principal:</h2>
  <div>
    <ul>
      <div id="div2">
        <li>Gestión de Tareas: </li> 
         Alta:<input type="radio" name="opcion" @click="TareaGAlta()" >   
         Baja:<input type="radio" name="opcion" @click="TareaGBaja()">
         Modificar:<input type="radio" name="opcion" @click="TareaGModi()">
      </div>
      <br>
      <div id="div1">
        <li>Asignación de Tareas: </li> 
         Alta:<input type="radio" name="opcion" @click="TareaAlta()" >   
         Baja:<input type="radio" name="opcion" @click="TareaBaja()">
         Modificar:<input type="radio" name="opcion" @click="TareaModi()">
      </div>
      <br>
      <li>Seguimiento <button @click="Seguimiento()">-></button></li>
      <li>Salir <button @click="Salir()">-></button></li>
    </ul>
  </div>
  <br>
  <Alta v-show="alta2"></Alta>
  <Baja v-show="baja"></Baja>
  <Modi v-show="modi"></Modi>
  <GAlta v-show="galta"></GAlta>
  <GBaja v-show="gbaja"></GBaja>
  <GModi v-show="gmodi"></GModi>
</template>
