<script setup>
 import Alta  from './components/Alta_Usuario_Tarea.vue'
 import Baja from './components/Baja_Usuario_Tarea.vue'
 import Modi from './components/Modi_Usuario_Tarea.vue'
 import GAlta from './components/GAlta.vue'
 import GBaja from './components/GBaja.vue'
 import GModi from './components/GModi.vue'
 import Tabla from './components/Tabla todos.vue'
 import TablaUsuarios from './components/Tabla usuarios.vue'
 import TablaSeleccionByUsers from './components/Tabla usuarios select.vue'
 import TablaSeleccionByTask from './components/Tabla tarea select.vue'
 import TablaSeleccionByEstate from './components/Tabla estado select.vue'
 import { ref } from 'vue';
 
 
 const alta2 = ref(false);
 const galta = ref(false);
 const gbaja = ref(false);
 const gmodi = ref(false);
 const ttodo = ref(true);
 const tuser = ref(false);
 const ttask = ref(false);
 const testate = ref(false);

 
 const baja = ref(false);

 const modi = ref(false);

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

  const seleccionarTablaUsuarios = () => {
       ttodo.value = false
       ttask.value = false
       tuser.value = true
       testate.value = false
  }

  const seleccionarTabla = () => {
       ttodo.value = true
       ttask.value = false
       tuser.value = false
       testate.value = false
  } 
  
  const seleccionarTablaTareas = () => {
       ttodo.value = false
       ttask.value = true
       tuser.value = false
       testate.value = false
  }
  
  const seleccionarTablaEstado = () => {
       ttodo.value = false
       ttask.value = false
       tuser.value = false
       testate.value = true
  } 

</script>

<style>
  h1{
    color: white;
    background-color: black;
    text-align: center;
    border-color: black;
    border-style: solid;
  }
  h3{
    color:grey
  }
  li{
    color:black
  }

  #div1{
    width: 30%;
    margin: 0px;
    border-color: lightblue;
    border-style: solid;
    background-color: white;
  }

  #div12{
     border-style: solid;
     border-color: white;
     background-color: lightblue;
   } 

  #div2{
    width: 30%;
    margin: 0px;
    border-color: lightblue;
    border-style: solid;
    background-color: white;
  }

  #div22{
     border-style: solid;
     border-color: white;
     background-color: lightblue;
   } 

   #div4{
    background-color: lightslategrey;
    width: 100%;
    margin: 0 auto;
    border-color: lightblue;
    border-style: solid;
    background-color: lightblue;
  }

   #div41{
     border-style: solid;
     border-color: white;
     background-color: lightblue;
   }  
  #div9{
    font-size: 15px; 
    text-align: center;  
    border-style: solid;
    border-color: black;
    background-color: white;
  } 

  

  #div3{
    width: 50%;
    margin: 0 auto;
    border-color: white;
    border-style: solid;
    background-color: lightslategrey;
  }

  

  
  
  #titulo{
    color: white;
    background-color: black;  
    border-style: solid;  
    border-color: black;
    border-color: white;
    align-items: center;
   }

  hr{
    height: 5px;
    background-color: black;

    border-color: black;
    border-style: solid;
  }
</style>

<template>
  <head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
  </head>
   <div id="div9">
    <h1 id="titulo">Gestión de Tareas:</h1>
   </div> 
     
  <div>

    <div>
        <h6>Usuarios conectados:</h6>
        <TablaUsuarios></TablaUsuarios>
      </div>
    <hr>
   
    <h2>Asignacion:</h2>
    <br>
     
    <ul>
        
      <div id="div2">
        <div id="div22">
          <li>Tareas: </li> 
           Alta:<input type="radio" name="opcion" @click="TareaGAlta()" >   
           Baja:<input type="radio" name="opcion" @click="TareaGBaja()">
           Modificar:<input type="radio" name="opcion" @click="TareaGModi()">
        </div>
      </div>
      <br>
      <div id="div1">
        <div id="div12">
          <li>Asignación de Tareas: </li> 
           Alta:<input type="radio" name="opcion" @click="TareaAlta()" >   
           Baja:<input type="radio" name="opcion" @click="TareaBaja()">
           Modificar:<input type="radio" name="opcion" @click="TareaModi()">
        </div> 
        </div>
      <br>
      
    </ul>
  </div>
  
  <br>
     <div id="div3">
      <Alta v-show="alta2"></Alta>
      <Baja v-show="baja"></Baja>
      <Modi v-show="modi"></Modi>
      <GAlta v-show="galta"></GAlta>
      <GBaja v-show="gbaja"></GBaja>
      <GModi v-show="gmodi"></GModi>
     </div>
     <br>
     <hr>
     <div id="tabla">
      <h2>Seguimiento:</h2>
      <ul>
        <div id="div4">
          <div id="div41">
            <li>Tipo de seleccion: </li> 
             Todos:<input type="radio" name="opcion" @click="seleccionarTabla()" >   
             Usuarios:<input type="radio" name="opcion" @click="seleccionarTablaUsuarios()">
             Tareas:<input type="radio" name="opcion" @click="seleccionarTablaTareas()">
             Estados:<input type="radio" name="opcion" @click="seleccionarTablaEstado()">
          </div>
        </div> 
      </ul>
      
      <TablaSeleccionByUsers v-show="tuser"></TablaSeleccionByUsers>
      <TablaSeleccionByTask v-show="ttask"></TablaSeleccionByTask>
      <Tabla v-show="ttodo"></Tabla>
      <TablaSeleccionByEstate v-show="testate"></TablaSeleccionByEstate>
     </div>
  
</template>
