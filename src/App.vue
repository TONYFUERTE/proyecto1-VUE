<script setup>

import { ref, computed } from 'vue';

const name = "Super Vue";
const contador = ref(0);
const arrayNumbers = ref([]);
// let arrayOrdenado = [];

const incrementar = () => {
    contador.value++;
};
const decrementar = () => {
    contador.value--;
};
const reset = () => {
    contador.value = 0;
};

const estilos = computed (() => { 
    if ( contador.value > 0) return "positivo";
    if ( contador.value < 0) return "negativo";
    if ( contador.value === 0 ) return "zero";
});

const add = () => {
        arrayNumbers.value.push(contador.value);
        console.log(arrayNumbers.value);
    };


const duplicados = computed (() => {

    let iguales = arrayNumbers.value.find((num) => num === contador.value);
    if (iguales || iguales === 0) return true;
    return false;
});

</script>

<template>
  
<div class="container text-center mt-5">
    <h1>Hola {{ name.toUpperCase() }}</h1><br>

    <h2 :class="estilos">{{ contador }}</h2>

<div class="btn-group mt-5">
    <button @click="incrementar" class="btn btn-success">Incrementar</button>
    <button @click="decrementar" class="btn btn-danger">Disminuir</button>
    <button @click="reset" class="btn btn-secondary">Reset</button>
    <button @click="add" :disabled="duplicados" class="btn btn-primary">Añadir valor</button>
</div>

   <p><span v-for="num in arrayNumbers">{{ num }},  </span></p>

<ul class="list-group">
  <li class="list-group-item" v-for="num in arrayNumbers">{{ num }}</li>
</ul>


</div>

</template>
<style>
h1 {
    color: red;
}

.positivo {
    color: blue;
}

.negativo {
    color: red;
}

.zero {
    color: green;
}
</style>