<script setup>
import { reactive } from 'vue';

  const estado = reactive({
    operacao: 'soma',
    numeroA: 0,
    numeroB: 0,
    resultado: 0
  })


 const getResultado = () => {
  const { operacao } = estado;
  switch (operacao) {
    case 'soma':
      return estado.resultado = (parseFloat(estado.numeroA) + parseFloat(estado.numeroB))
    case 'subtrair':
      return estado.resultado = (parseFloat(estado.numeroA) - parseFloat(estado.numeroB))
    case 'dividir':
      return estado.resultado = (parseFloat(estado.numeroA)  / parseFloat(estado.numeroBB))
    case 'multiplicar':
      return estado.resultado = (parseFloat(estado.numeroA) * parseFloat(estado.numeroB))
  }

 }
</script>

<template>
  <div class="container">
    <header>
    <h1 class="p-5 mb-1 my-4 bg-info text-center">Calculadora</h1>
    <p>Soma, subtração, divisão e multiplicação</p>
  </header>
  <div class="mt-5 mb-5 d-flex justify-content-around">
    <div class="mb-3">
      <input @change="evento => estado.numeroA = evento.target.value" type="number" placeholder="Digite aqui o numero">
    </div>
    <div>
        <select @change="evento => estado.operacao = evento.target.value">
          <option value="soma">Somar</option>
          <option value="subtrair">Subtrair</option>
          <option value="dividir">Dividir</option>
          <option value="multiplicar">Multiplicar</option>
        </select>
    </div>
    <div>
      <input @change="evento => estado.numeroB = evento.target.value" type="number" placeholder="Digite aqui o numero">
    </div>
  </div>
  <div class="col-md-12">
    <p @change="evento => estado.resultado = evento.target.value" class="fw-bold fs-6 text-center mt-5">
      O Resultado é {{ getResultado() }}
    </p>
  </div>
  </div>
</template>
<style scoped>

</style>
