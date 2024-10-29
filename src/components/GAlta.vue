
<template>
    
    
    <form>
        <h3>Crear Tarea:</h3>
          <br>
          Ingrese Tarea:<input v-model="nueva" id="t1">
          <br>
          <br>
          <button @click="cargar()">Crear</button>
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
    import { ref } from 'vue';
 
    const nueva = ref();
    const cargar = async  () => {
        
        const options = {
            method: 'POST',
            headers: {
                'Content-Type': 'application/json'
            },
            body: JSON.stringify({
            descripcion: nueva.value,
            habilitado: true,
        })
        };


        const response = await fetch('http://localhost:3000/tareas', options);
        if (response.ok) {
           alert('Tarea creada');
        } else {
            alert('Error al crear la tarea');
        }
    }

    
</script>