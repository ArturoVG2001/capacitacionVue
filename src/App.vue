<script setup>
import { computed, ref } from 'vue';
const name = 'vue dinamico';
let counter = ref(0);
let numberArray = ref([]);
let disabledBand = ref(false);

const increment = () => (counter.value++);

const decrement = () => (counter.value--);

const restart = () => (counter.value = 0);

const classCounter = () => {
  if (counter.value === 0) {
    return 'zero';
  } else if (counter.value > 0) {
    return 'positive';
  } else {
    return 'negative';
  }
}

const pushNumber = () => {
  if (numberArray.value.includes(counter.value)) {
    disabledBand.value = true;
  } else {
    numberArray.value.push(counter.value)
    disabledBand.value = false;
  }
}

</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}</h1><br>
    <h2 :class="classCounter()">{{ counter }}</h2>
    <div class="btn-group">
      <button @click="decrement" class="btn btn-success">Disminuir</button>
      <button @click="restart" class="btn btn-danger">Reiniciar</button>
      <button @click="increment" class="btn btn-secondary">Aumentar</button>
      <button @click="pushNumber()" :disabled="disabledBand" class="btn btn-primary">Add</button>
    </div>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(num, index) in numberArray" :key="index">{{ num }}</li>
    </ul>
  </div>
</template>

<style>
.positive {
  color: green;
}

.negative {
  color: red;
}

.zero {
  color: peru;
}
</style>