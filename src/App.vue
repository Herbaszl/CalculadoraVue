<script setup>
import { reactive } from 'vue';


const estado = reactive({
num1: 0,
num2: 0,
operacao: 'soma',
resultado: 0,})

const calcular = () => {
  const { num1, num2, operacao } = estado;
  switch (operacao) {
    case 'soma':
      estado.resultado = parseFloat(num1) + parseFloat(num2);
      break;
    case 'subtracao':
      estado.resultado = parseFloat(num1) - parseFloat(num2);
      break;
    case 'multiplicacao':
      estado.resultado = parseFloat(num1) * parseFloat(num2);
      break;
    case 'divisao':
      estado.resultado = parseFloat(num1) / parseFloat(num2);
      break;
    default:
      estado.resultado = 0;
  }
};
</script>

<template>
  <div class="calculadora">
    <div class="resultado">
      <p>{{ estado.resultado }}</p>
    </div>
    <input @input="estado.num1 = $event.target.value; calcular()" type="number" class="input" placeholder="00">
    <select @change="estado.operacao = $event.target.value; calcular()" class="select-operacao">
      <option value="soma">+</option>
      <option value="subtracao">-</option>
      <option value="multiplicacao">×</option>
      <option value="divisao">÷</option>
    </select>
    <input @input="estado.num2 = $event.target.value; calcular()" type="number" class="input" placeholder="00">
  </div>
</template>

<style scoped>
.calculadora {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #8f8445;
  border-radius: 8px;
  padding: 20px;
  width: 300px;
  margin: auto;
  margin-top: 50px;
  font-family: Arial, sans-serif;
}

.resultado {
  background-color: #eedf9c;
  color: #000;
  width: 100%;
  padding: 15px;
  border-radius: 8px;
  text-align: right;
  font-size: 1.5em;
  margin-bottom: 20px;
}

.input, .select {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  font-size: 1.2em;
  border: 1px solid #ccc;
  border-radius: 8px;
}

.select-operacao {
  width: 100%;
  padding: 10px;
  margin: 10px 0;
  font-size: 1.2em;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: #fff;}
  
</style>
