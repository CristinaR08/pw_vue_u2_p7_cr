<template>
  <h2>{{ encabezado }} : {{ valor2 }}</h2>
  <p>{{ numero }} <sup>2</sup>={{ calcularComputadoCuadrado }}</p>
  <p>{{ numero }} <sup>2</sup>={{ calcularComputadoCuadrado }}</p>
  <div>
    <button @click="incrementar()">+1</button>
    <button v-on:click="decrementar()">-1</button>
  </div>
  <div v-if="esVerdad">
    <h1>Feliz Navidad</h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero: this.valor,
      titulo: 'Contador'
    }
  },
  methods: {
    calcularCuadrado() {
      console.log("Entro a calcular");
      return this.numero * this.numero;
    },
    incrementar() {
      this.numero++;
    },
    decrementar() {
      this.numero--;
    },
  },
  computed: {
    calcularComputadoCuadrado() {
      console.log("Entro a calcular computada");
      return this.numero * this.numero;
    },
  },
  //props: ['encabezado', 'valor']
  props:{
    //encabezado: String,
    encabezado:{
      type: String,
      validator(value){
        let cadena = "a";
        return !value.includes(cadena);
      },
    },
    valor: Number,
    valor2:{
      type: Number,
      required: false,
      default: 77,
      validator(value){
        //programo mi validacion bajo mi criterio y 
        //retorno true cuando es válido para mi y 
        //retorno false cuando no lo es.
        return value<=77;
      },
    },
    esVerdad:{
      type: Boolean,
      required: true,
    },
    arreglo: Array,
    fecha: Date,
    objetoPersona: Object,
  },
}
</script>

<style>
button {
  background: #64B687;
  border-radius: 15px;
  border: 5px outset green;
  margin: 0px 5px;
  padding: 5px 10px;
  font-size: 20px;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
}

button:hover {
  background: #5aa67b;
  color: aliceblue;
}
</style>