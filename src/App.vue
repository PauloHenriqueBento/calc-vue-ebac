<script setup>
import { reactive} from 'vue';

import Inputs from './components/Inputs.vue';

const store = reactive({
  number1: 0,
  number2: 0,
  operation: 'add',
});

function calculateResult() {
  switch (store.operation) {
    case 'add':
      return store.number1 + store.number2;
    case 'subtract':
      return store.number1 - store.number2;
    case 'multiply':
      return store.number1 * store.number2;
    case 'divide':
      return store.number2 !== 0
        ? (store.number1 / store.number2).toFixed(2)
        : 'Erro: Divisão por zero';
    default:
      return 0;
  }
}
</script>

<template>
  <div class="container mt-5">
    <h1 class="text-center mb-4">Calculadora Aritmética</h1>

    <Inputs 
        :number1="store.number1" 
        :number2="store.number2" 
        :operation="store.operation" 
        @updateNumber1="store.number1 = $event" 
        @updateNumber2="store.number2 = $event" 
        @updateOperation="store.operation = $event" 
    />

    <div class="text-center">
      <h2>Resultado: {{ calculateResult() }}</h2>
    </div>
  </div>
</template>
