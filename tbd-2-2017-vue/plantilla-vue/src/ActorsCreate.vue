<template>
  <div class="center">

      <h1>Crear Actor</h1>

      <div>
        <h3>Nombre</h3>
        <input type="text" name="nombre" v-model="actor.firstName" required>
      </div>
      <div>
        <h3>Apellido</h3>
        <input type="text" name="Apellido"  v-model="actor.lastName" required>
      </div>


      <button v-on:click.prevent="post" type="submit" name="agregar"> Aceptar </button>


  </div>
</template>


<script>

export default {
  data(){
    return{
      actor:{
        firstName:'',
        lastName:''
      }
    }
  },
  methods: {
    post:function(){
      var actor = this.actor
      this.actor = {firstName:'' , lastName:''}
      this.$http.post('http://localhost:8081/sakila-spring-backend/actors', actor
      ).then(function(data){
        console.log(data);
      },response => {
    // error callback
      });
    }
  }
}



</script>

