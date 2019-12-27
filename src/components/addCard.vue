<template>

<form
  id="app"
  @submit="checkForm"
  action="https://vuejs.org/"
  method="post"
>

  <p v-if="errors.length">
    <b>Por favor, corrija el(los) siguiente(s) error(es):</b>
    <ul>
      <li v-for="(error,index) in errors" :key="index">{{ error }}</li>
    </ul>
  </p>

  <p>
    <label for="name">Nombre</label>
    <input
      id="name"
      v-model="name"
      type="text"
      name="name"
    >
  </p>

  <p>
    <label for="age">Edad</label>
    <input
      id="age"
      v-model="age"
      type="number"
      name="age"
      min="0">
  </p>

  <p>
    <label for="movie">Película favorita</label>
    <select
      id="movie"
      v-model="movie"
      name="movie"
    >
      <option>Star Wars</option>
      <option>Vanilla Sky</option>
      <option>Atomic Blonde</option>
    </select>
  </p>

  <p>
    <input
      type="submit"
      value="Enviar"
    >
  </p>

</form>


</template>

<script>
// import * from './reusable/cardsBase'



export default {
  name: 'addCard',
  data:function () {
    return {
        errors: [],
        name: null,
        age: null,
        movie: null
    }
  },
  methods:{
    checkForm: function (e) {
      if (this.name && this.age) {
        return true;
      }

      this.errors = [];

      if (!this.name) {
        this.errors.push('El nombre es obligatorio.');
      }
      if (!this.age) {
        this.errors.push('La edad es obligatoria.');
      }

      e.preventDefault();
    }
  }
  
}



</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .defaultColor{
    color:#52d03e
  }

  .textDefaultAction{
    color:#43689e;
    text-decoration:underline;
    padding:6px  }


</style>
