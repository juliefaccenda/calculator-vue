<template>
  <div class="row justify-content-md-center">
    <div class="col-3">
      <div class="calculadora">
        <div class="display form-control">{{ atualValue || "0" }}</div>
        <div @click="cleanCalculator" class="botao btn btn-info">C</div>
        <div @click="changeSignal" class="botao btn btn-info">+/-</div>
        <div @click="percentValue" class="botao btn btn-info">%</div>
        <div @click="division" class="botao operadores btn btn-info">÷</div>
        <div class="w-100"></div>
        <div @click="setValue('7')" class="botao btn btn-light">7</div>
        <div @click="setValue('8')" class="botao btn btn-light">8</div>
        <div @click="setValue('9')" class="botao btn btn-light">9</div>
        <div @click="multiply" class="botao operadores btn btn-info">x</div>
        <div class="w-100"></div>
        <div @click="setValue('4')" class="botao btn btn-light">4</div>
        <div @click="setValue('5')" class="botao btn btn-light">5</div>
        <div @click="setValue('6')" class="botao btn btn-light">6</div>
        <div @click="dim" class="botao operadores btn btn-info">-</div>
        <div class="w-100"></div>
        <div @click="setValue('1')" class="botao btn btn-light">1</div>
        <div @click="setValue('2')" class="botao btn btn-light">2</div>
        <div @click="setValue('3')" class="botao btn btn-light">3</div>
        <div @click="sum" class="botao operadores btn btn-info">+</div>
        <div class="w-100"></div>
        <div class="botao btn btn-info">.</div>
        <div @click="setValue('0')" class="botao btn btn-light">0</div>
        <div @click="result" class="botao btn btn-info">=</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      atualValue: "",
      lastValue: null,
      operationType: null,
      operationSelect: false,
    };
  },
  methods: {
    //   atribui o valor vazio para o valor atual
    cleanCalculator() {
      this.atualValue = "";
    },
    setValue(n) {
      // se clicar em algum operador, retorna valor vazio e false
      if (this.operationSelect) {
        this.atualValue = "";
        this.operationSelect = false;
      }
      this.atualValue = `${this.atualValue}${n}`;
    },
    changeSignal() {
      //O método charAt() retorna o caractere especificado a partir de uma string. -
      // O método slice() retorna uma cópia de parte de um array a partir de um subarray criado
      this.atualValue =
        this.atualValue.charAt(0) === "-"
          ? this.atualValue.slice(1)
          : `-${this.atualValue}`;
    },
    percentValue() {
      this.atualValue = `${parseFloat(this.atualValue) / 100}`;
    },
    setLastValue() {
      this.lastValue = this.atualValue;
      this.operationSelect = true;
    },
    division() {
      this.operationType = (num1, num2) => num1 / num2;
      this.setLastValue();
    },
    sum() {
      this.operationType = (num1, num2) => num1 + num2;
      this.setLastValue();
    },
    multiply() {
      this.operationType = (num1, num2) => num1 * num2;
      this.setLastValue();
    },
    dim() {
      this.operationType = (num1, num2) => num1 - num2;
      this.setLastValue();
    },
    result() {
      this.atualValue = `${this.operationType(
        parseFloat(this.lastValue),
        parseFloat(this.atualValue)
      )}`;
      this.lastValue = null;
    },
  },
};
</script>

<style>
</style>