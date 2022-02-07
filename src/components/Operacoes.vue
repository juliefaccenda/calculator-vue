<template>
  <div class="row justify-content-md-center">
    <div class="col-3">
      <div class="calculadora">
        <div class="display form-control">{{ valorAtual || "0" }}</div>
        <div @click="limparCalculadora" class="botao btn btn-info">C</div>
        <div @click="atribuiValor" class="botao btn btn-info">+/-</div>
        <div @click="atribuiValor" class="botao btn btn-info">%</div>
        <div @click="atribuiValor" class="botao btn btn-info">%</div>
        <div class="w-100"></div>
        <div @click="atribuiValor('7')" class="botao btn btn-light">7</div>
        <div @click="atribuiValor('8')" class="botao btn btn-light">8</div>
        <div @click="atribuiValor('9')" class="botao btn btn-light">9</div>
        <div class="botao operadores btn btn-info">÷</div>
        <div class="w-100"></div>
        <div @click="atribuiValor('4')" class="botao btn btn-light">4</div>
        <div @click="atribuiValor('5')" class="botao btn btn-light">5</div>
        <div @click="atribuiValor('6')" class="botao btn btn-light">6</div>
        <div class="botao operadores btn btn-info">x</div>
        <div class="w-100"></div>
        <div @click="atribuiValor('1')" class="botao btn btn-light">1</div>
        <div @click="atribuiValor('2')" class="botao btn btn-light">2</div>
        <div @click="atribuiValor('3')" class="botao btn btn-light">3</div>
        <div class="botao operadores btn btn-info">-</div>
        <div class="w-100"></div>
        <div @click="atribuiValor" class="botao btn btn-info">.</div>
        <div @click="atribuiValor('0')" class="botao btn btn-light">0</div>
        <div class="botao btn btn-info">=</div>
        <div class="botao operadores btn btn-info">+</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      valorAtual: "",
    };
  },
  methods: {
    //   atribui o valor vazio para o valor atual
    limparCalculadora() {
      this.valorAtual = "";
    },
    atribuiValor(n) {
      this.valorAtual = this.valorAtual + n;
    },
  },
};
</script>

<style>
</style>