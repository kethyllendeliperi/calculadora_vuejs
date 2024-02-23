<script setup>
import { defineProps } from 'vue';

const { estado, operacaoMuda, primeiroValorMuda, segundoValorMuda } = defineProps(['estado', 'operacaoMuda', 'primeiroValorMuda', 'segundoValorMuda']);
</script>

<template>
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
</template>
