
<template>
    
    
    <form>
        <h3>Alta:</h3>
          <ID @seleccion="tomarValor"></ID> Usuario:<input>
          <br>
          Usuario:<input>
          <br>
          Ingrese Tarea:<input>
          <br>
          <button @click="crear()">Crear</button>
          <button>Salir</button>
    
    </form>
    
</template>

<style scoped>
   form {
    color: black;
    background-color: rgb(75, 82, 148);
    border-style: solid;
    border-color: black
   }
   h3{
    color: white;
    background-color: rgb(1, 1, 26);
   }
</style>

<script setup>
    import ID from "../components/Select_ID.vue"
    import { ref } from 'vue';
    const valorID = ref('');
    //const cone = async function conexion(){
        
        const tomarValor = (valor) =>{
            valorID.value = valor;
            alert(valorID.value);
        }
       

      
        
//}
</script>