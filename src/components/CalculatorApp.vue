<template>
  <div class="calculatorApp">
    <h1 class="text-2xl font-bold mb-4">Calculadora</h1>
    <input v-model.number="num1" type="number" placeholder="Número 1" class="input-field" />
    <input v-model.number="num2" type="number" placeholder="Número 2" class="input-field" />
    <div class="buttons">
      <button @click="calculate('+')">+</button>
      <button @click="calculate('-')">-</button>
      <button @click="calculate('*')">*</button>
      <button @click="calculate('/')">/</button>
    </div>
    <h2 class="result">Resultado: {{ result }}</h2>
    
    <h2 class="history-title">Historial de Cálculos</h2>
    <ul class="history">
      <li v-for="(entry, index) in history" :key="index">{{ entry }}</li>
    </ul>
  </div>
</template>

<script>
export default {
 name: "CalculatorApp",
  data() {
    return {
      num1: 0,
      num2: 0,
      result: 0,
      history: []
    };
  },
  methods: {
    calculate(operator) {
      let operationResult;
      switch (operator) {
        case '+':
          operationResult = this.num1 + this.num2;
          break;
        case '-':
          operationResult = this.num1 - this.num2;
          break;
        case '*':
          operationResult = this.num1 * this.num2;
          break;
        case '/':
          operationResult = this.num2 !== 0 ? this.num1 / this.num2 : 'Error';
          break;
      }
      this.result = operationResult;
      this.history.unshift(`${this.num1} ${operator} ${this.num2} = ${operationResult}`);
    }
  }
};
</script>

<style scoped>
.calculatorApp {
  text-align: center;
  max-width: 300px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.1);
}
.input-field {
  width: 100%;
  padding: 8px;
  margin: 10px 0;
  border: 1px solid #ccc;
  border-radius: 5px;
}
.buttons button {
  margin: 5px;
  padding: 10px;
  border: none;
  background-color: #007bff;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}
.buttons button:hover {
  background-color: #0056b3;
}
.result {
  font-size: 20px;
  margin-top: 10px;
}
.history-title {
  font-size: 18px;
  margin-top: 20px;
  font-weight: bold;
}
.history {
  list-style: none;
  padding: 0;
  max-height: 150px;
  overflow-y: auto;
  border-top: 1px solid #ddd;
  margin-top: 10px;
}
.history li {
  padding: 5px;
  border-bottom: 1px solid #ddd;
}
</style>
