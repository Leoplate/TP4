<template>
  
     <div>
        N° ID:
        <select>
            <option v-for="opcion in Base" :key="opcion.id" :value="opcion.id">
                {{ opcion.id }}
            </option>
        </select>
        
      </div> 
    
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

<script>
    
    export default {
    data() {
        return {
            Base: [],
        };
    },
    async mounted() {
    
        const options = {
            method: 'GET',
            headers: {
                'Content-Type': 'application/json'
            }
        };
        const response = await fetch('http://localhost:3000/tareas', options);
        this.Base = await response.json();
    },
    
};
      

      
        
</script>