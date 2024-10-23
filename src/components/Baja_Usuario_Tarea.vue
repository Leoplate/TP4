
<template>
    
    
    <form>
        <h3>Baja:</h3>
        <br>
          N° ID Asignación:
        <select v-model="ida" @change="cambiarDescripcion">
            <option v-for="opcion in BaseA" :key="opcion.id" :value="opcion.id" >
                {{ opcion.id }}
            </option>
        </select>
          <br>
          Usuario:<input v-model="descripcionU" id="t1u">
          
          Tarea:<input v-model="descripcion" id="t1">
            
          Estado:<select v-model="estado" name="estado" >
            <option value="1">1-Pendiente</option>
            <option value="2">2-En progreso</option>
            <option value="3">3-Completada</option>
          </select>
          <br>
          <button @click="eliminar()">Eliminar</button>
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
const idu = ref('');
const ida = ref('');
const estado = ref('');
const Base = ref([]);
const BaseU = ref([]);
const BaseA = ref([]);
const descripcion = ref('');
const descripcionU = ref('');

const eliminar = async () => {
    const options = {
        method: 'DELETE',
        headers: {
            'Content-Type': 'application/json'
        },
        //body: JSON.stringify({
        //    id_usuario: idu.value,
        //    id_tarea: idt.value,
        //})
    };
        
    const response = await fetch('http://localhost:3000/asignar/'+ ida.value, options);
    if (response.ok) {
        alert('Asignación eliminada');
    } else {
        alert('Error al eliminar la asignación');
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
    const responseUsuario = await fetch('http://localhost:3000/usuarios', options);
    BaseU.value = await responseUsuario.json();
    const responseAsignacion = await fetch('http://localhost:3000/asignar', options);
    BaseA.value = await responseAsignacion.json();
});
    
const cambiarDescripcion = () => {
    
    
    const seleA = BaseA.value.find(opcion => opcion.id === ida.value);
    
    const selectedOption = Base.value.find(opcion => opcion.id === seleA.id_tarea);
    
    if (selectedOption) {
        descripcion.value = selectedOption.descripcion;
    }

    const selectedOptionU = BaseU.value.find(opcion => opcion.id === seleA.id_usuario);
    
    if (selectedOptionU) {
        descripcionU.value = selectedOptionU.nombre + " "+selectedOptionU.apellido;
    }

    estado.value = seleA.id_estado
}
    

</script>