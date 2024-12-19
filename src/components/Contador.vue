<template>
  <h2>{{ titulo }}</h2>
  <p>{{ numero }} <sup>2</sup>={{ calcularComputadoCuadrado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularComputadoCuadrado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularComputadoCuadrado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularComputadoCuadrado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularComputadoCuadrado }}</p>
  <div>
    <button v-on:click="incrementar()">+1</button>
    <button v-on:click="decrementar()">-1</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero: 25,
      titulo: 'Contador'
    }
  },
  methods: {
    calcularCuadrado() {
      console.log("Entro a calcular");
      return this.numero * this.numero;
    },
    incrementar(){
      this.numero++;
    },
    decrementar(){
      this.numero--;
    },
  },
  computed:{
    calcularComputadoCuadrado() {
      console.log("Entro a calcular computada");
      return this.numero * this.numero;
    },
  },
}
</script>

<style>
button{
  background: #64B687;
  border-radius: 15px;
  border: 5px outset green;
  margin: 0px 5px;
  padding: 5px 10px;
  font-size: 20px;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}
button:hover{
  background: #5aa67b;
  color: aliceblue;
}
</style>