<script setup>
  import { reactive } from 'vue';

  const estado = reactive({
    operacao: '',
    numero1: 0,
    numero2: 0,
    total: 0
  })

  const calcular = (number2) => {
    estado.numero2 = number2;

    const { numero1, numero2 } = estado

    switch (estado.operacao){
      case 'soma':
        return estado.total = numero1 + numero2
      case 'subtracao':
        return estado.total = numero1 - numero2
      case 'multiplicacao':
        return estado.total = numero1 * numero2
      case 'divisao':
        return estado.total = numero1 / numero2
      default:
        alert('Selecione uma operação.')
    }
  }
</script>

<template>
  <div class="container">
    <h1 class="mt-4">Calculadora</h1>
    <div class="row">
      <div class="col-3">
        <p>Primeiro número:</p>
      </div>
      <div class="col-3">
        <p>Operação</p>
      </div>
      <div class="col-3">
        <p>Segundo número</p>
      </div>
      <div class="col-3">
        Resultado
      </div>
    </div>
    <div class="row">
      <div class="col-3">
        <input type="number" name="number1" id="number1" class="form-control" @keyup="event => estado.numero1 = Number(event.target.value)">
      </div>
      <div class="col-3">
        <select name="operacao" id="operacao" class="form-control" @change="event => estado.operacao = event.target.value">
          <option value="selecione">Selecione</option>
          <option value="soma">Soma</option>
          <option value="subtracao">Subtração</option>
          <option value="multiplicacao">Multiplicação</option>
          <option value="divisao">Divisão</option>
        </select>
      </div>
      <div class="col-3">
        <input @keyup="event => calcular(Number(event.target.value))" type="number" name="number2" id="number2" class="form-control">
      </div>
      <div class="col-3">
        <span v-if="{{estado.total}} === NaN"> 0 </span>
        <span v-else>{{ estado.total }}</span>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
