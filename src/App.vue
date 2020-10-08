<template>
  <div id="app">
    <form @submit.prevent="agregarTarea">
      <label for="tarea">Inserte una tarea:  </label>
      <input type="text" v-model="tarea">
      <button type="submit">Agregar</button>
    </form>
    <div>
      <ul>
        <li v-for="(task,index) in tareas" :key="index">{{task}} 
        <button @click="eliminar(index)" class="elimina">☑</button> </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return{
      tarea: '',
      tareas: [],
    }
  },
  methods: {
    agregarTarea(){
        this.tareas.push(this.tarea);
        this.tarea = '';
    },
    eliminar(valor){
      let confirmado = confirm("¿Ya realizaste esta tarea?:O")
      if (confirmado){
        this.tareas.splice(valor,1);
        alert("Se eliminó...");
      }
    },
  }
}
</script>

<style>

</style>
