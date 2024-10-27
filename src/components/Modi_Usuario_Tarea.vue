
<template>
    
    
    <form>
        <h3>Modificar:</h3>
        N° ID Asignación:
        <select v-model="ida" @change="cambiarDescripcionI">
            <option v-for="opcion in BaseA" :key="opcion.id" :value="opcion.id" >
                {{ opcion.id }}
            </option>
        </select>
        <br>
        <br>
          N° ID Usuario:
        <select v-model="idu" @change="cambiarDescripcionU">
            <option v-for="opcion in BaseU" :key="opcion.id" :value="opcion.id" >
                {{ opcion.id}}
            </option>
        </select>
          Usuario:<input v-model="descripcionU" id="t1u">
          <br>

          <br>
          N° ID Tarea:
        <select v-model="idt" @change="cambiarDescripcionT">
            <option v-for="opcion in Base" :key="opcion.id" :value="opcion.id" >
                {{ opcion.id + "-" + opcion.descripcion }}
            </option>
        </select>
          Tarea:<input v-model="descripcion" id="t1">
          <br>
          <br>
          Estado:
          <select v-model="ide" @change="cambiarDescripcionE">
            <option v-for="opcion in BaseE" :key="opcion.id" :value="opcion.id" >
                {{ opcion.id + "-" + opcion.descripcion}}
            </option>
        </select>
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
const idu = ref('');
const ide = ref('');
const ida = ref('');

const Base = ref([]);
const BaseU = ref([]);
const BaseE = ref([]);
const BaseA = ref([]);
const descripcion = ref('');
const descripcionU = ref('');
const descripcionE = ref('');

const modificar = async () => {
    const options = {
        method: 'PUT',
        headers: {
            'Content-Type': 'application/json'
        },
        body: JSON.stringify({
            id_usuario: idu.value,
            id_tarea: idt.value,
            id_estado: ide.value,
        })
    };
        
    const response = await fetch('http://localhost:3000/asignar/' + ida.value, options);
    if (response.ok) {
        alert('Tarea asignada');
    } else {
        alert('Error al asignar la tarea');
    }
};

onMounted(async () => {
    const options = {
        method: 'GET',
        headers: {
            'Content-Type': 'application/json'
        }
    };
    const responseAsignacion = await fetch('http://localhost:3000/asignar', options);
    BaseA.value = await responseAsignacion.json();
    const response = await fetch('http://localhost:3000/tareas', options);
    Base.value = await response.json();
    const responseUsuario = await fetch('http://localhost:3000/usuarios', options);
    BaseU.value = await responseUsuario.json();
    const responseEstado = await fetch('http://localhost:3000/estados', options);
    BaseE.value = await responseEstado.json(); 
});
    

const cambiarDescripcionT = () => {
    
    
    const selectedOption = Base.value.find(opcion => opcion.id === idt.value);
    
    if (selectedOption) {
        descripcion.value = selectedOption.descripcion;
        
    }

}    
    

const cambiarDescripcionU = () => {
  const selectedOptionU = BaseU.value.find(opcion => opcion.id === idu.value);
    
    if (selectedOptionU) {
        descripcionU.value = selectedOptionU.nombre + " "+selectedOptionU.apellido;
        
    }

}

const cambiarDescripcionE = () => {

    const selectedOptionE = BaseE.value.find(opcion => opcion.id === ide.value);
         
    if (selectedOptionE) {
        descripcionE.value = selectedOptionE.id + "-"+selectedOptionE.descripcion;
        
    }
}


const cambiarDescripcionI = () => {
    
    
    const seleA = BaseA.value.find(opcion => opcion.id === ida.value);
    
    const selectedOption = Base.value.find(opcion => opcion.id === seleA.id_tarea);
    
    if (selectedOption) {
        descripcion.value = selectedOption.descripcion;
        idt.value = seleA.id_tarea;
    }

    const selectedOptionU = BaseU.value.find(opcion => opcion.id === seleA.id_usuario);
    
    if (selectedOptionU) {
        descripcionU.value = selectedOptionU.nombre + " "+selectedOptionU.apellido;
        idu.value = seleA.id_usuario;
    }

    const selectedOptionE = BaseE.value.find(opcion => opcion.id === seleA.id_estado);
         
    if (selectedOptionE) {
        descripcionE.value = selectedOptionE.id + "-"+selectedOptionE.descripcion;
        ide.value = seleA.id_estado;
    }
}
    

</script>