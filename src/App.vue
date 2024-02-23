<script setup>
import { reactive } from 'vue';
import Formulario from './components/Formulario.vue';

const estado = reactive({
  operacao: 'adicao',
  primeiroValor: 0,
  segundoValor: 0,
  resultado: 0,
});

function operacaoMuda(evento) {
  estado.operacao = evento.target.value;
  calcularResultado();
}

function primeiroValorMuda(evento) {
  estado.primeiroValor = evento.target.value;
  calcularResultado();
}

function segundoValorMuda(evento) {
  estado.segundoValor = evento.target.value;
  calcularResultado();
}

function calcularResultado() {
  switch (estado.operacao) {
    case 'adicao':
      estado.resultado = Number(estado.primeiroValor) + Number(estado.segundoValor);
      break;
    case 'subtracao':
      estado.resultado = Number(estado.primeiroValor) - Number(estado.segundoValor);
      break;
    case 'multiplicacao':
      estado.resultado = Number(estado.primeiroValor) * Number(estado.segundoValor);
      break;
    case 'divisao':
      estado.resultado = Number(estado.primeiroValor) / Number(estado.segundoValor);
      break;
    default:
      estado.resultado = 0;
  }
}
</script>

<template>
  <div class="row justify-content-center text-body-tertiary">
    <header class="p-5 mb-2 mt-2 text-info">
    <h1> Calculadora aritmética </h1>
  </header>
    <div class="col-md-4">
      <Formulario :estado="estado" :operacaoMuda="operacaoMuda" :primeiroValorMuda="primeiroValorMuda" :segundoValorMuda="segundoValorMuda" />
    </div>
  </div>
</template>

<style scoped></style>