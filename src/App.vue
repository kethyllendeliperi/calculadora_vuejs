<script setup>
import { reactive } from 'vue';

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
  <div class="container text-center border border-info mt-4">
    <header class="p-5 mb-2 mt-2 text-info">
      <h1>Calculadora aritmética</h1>
    </header>
    <div class="row justify-content-center text-body-tertiary">
      <div class="col-md-4">
        <form>
          <label for="operacao" class="fw-bold mb-2">Escolha uma operação:</label>
          <select :value="estado.operacao" @input="operacaoMuda" class="form-control text-center mb-3">
            <option value="adicao">+</option>
            <option value="subtracao">-</option>
            <option value="multiplicacao">*</option>
            <option value="divisao">/</option>
          </select>
          <div class="col">
            <label for="primeiroValor" class="fw-bold mb-1">Insira o primeiro valor: </label>
            <input :value="estado.primeiroValor" @input="primeiroValorMuda" type="number" class="mb-3 form-control">
          </div>
          <div class="col">
            <label for="segundoValor" class="fw-bold mb-1">Insira o segundo valor: </label>
            <input :value="estado.segundoValor" @input="segundoValorMuda" type="number" class="mb-3 form-control">
          </div>
          <div class="col">
            <label for="resultado" class="fw-bold mb-1">Resultado: </label>
            <input :value="estado.resultado" type="number" class="mb-5 form-control">
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>