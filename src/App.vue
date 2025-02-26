<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numero_a: '',
  numero_b: '',
  resultado:0,
  operador:'',
})

function calcula (){
  const {numero_a ,numero_b, operador} = estado
  const a = Number(numero_a)
  const b = Number(numero_b)

  if(operador == "+"){
    return a + b
  }else if(operador == "-"){
    return a - b
  }else if(operador == "*"){
    return a * b
  }else if(operador == "/"){
    if (b  > 0){
      return a / b
    }else{
      return alert("Não é possível dividir por zero")
    }
  }
}
</script>

<template>
<div class="container">
  <header class="p-5 mb-4 mt-4 bg-light rounded-3">
    <h1>Calculadora Aritmética</h1>
  </header>
</div>
<div class="container">
  <h2 class="p-5 mb-4 mt-4 bg-light rounded-3">Resultado {{ calcula() }}</h2>
</div>
<div class="container">
  <form>
    <input @keyup="evento => estado.numero_a = evento.target.value" type="number" placeholder="Digite o Primeiro Numero" class="form-control mb-2">
    <select @change="evento => estado.operador = evento.target.value" class="form-control mb-2">
      <option selected value="">Selecione um Operador</option>
      <option value="+">Adição</option>
      <option value="-">Subtração</option>
      <option value="*">Multiplicação</option>
      <option value="/">Divisão</option>
    </select>
    <input @keyup="evento => estado.numero_b = evento.target.value" type="number" placeholder="Digite o Segundo Numero" class="form-control mb-2">
  </form>
</div>
</template>

<style scoped>

</style>

