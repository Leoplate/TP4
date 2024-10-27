
<template>
    
    
    <form>
        <h3>Modificar Tarea:</h3>
          <br>
          N° ID:
        <select v-model="idt" @change="cambiarDescripcion">
            <option v-for="opcion in Base" :key="opcion.id" :value="opcion.id" >
                {{ opcion.id + "-" + opcion.descripcion }}
            </option>
        </select>
          Tarea:<input v-model="descripcion" id="t1">
          <br>
          <br>
          <button @click="modificar()">Modificar</button>
          <button>Salir</button>
    
    </form>
    
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
</style>

<script setup>
    import { ref, onMounted } from 'vue';

const idt = ref('');
const Base = ref([]);
const descripcion = ref('');

const modificar = async () => {
    const options = {
        method: 'PUT',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            descripcion: descripcion.value,
            habilitado: true,
        })
    };
        
    const response = await fetch('http://localhost:3000/tareas/' + idt.value, options);
    if (response.ok) {
        alert('Tarea modificada');
    } else {
        alert('Error al modificar la tarea');
    }
};

onMounted(async () => {
    const options = {
        method: 'GET',
        headers: {
            'Content-Type': 'application/json'
        }
    };
    const response = await fetch('http://localhost:3000/tareas', options);
    Base.value = await response.json();
});
    
const cambiarDescripcion = () => {
    
    const selectedOption = Base.value.find(opcion => opcion.id === idt.value);
    
    if (selectedOption) {
        descripcion.value = selectedOption.descripcion;
    }
}
    

</script>