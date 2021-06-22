<template>
  <img class="cifrao-logo" src="/images/sifrao-de-dinheiro.png" alt="vue logo" />
  <h1>Conversor de Reais para dólares</h1>

  <div class="div-convensor">
    <span class="p-float-label">
      <InputText id="input-reais" type="text" v-model="reais" v-bind:disabled="conversor" />
      <label for="input-reais">Quantidade em Reais</label>
    </span>
  </div>

  <div class="div-convensor">
    <span class="p-float-label">
      <InputText id="input-dolar" type="text" v-model="dolar" v-bind:disabled="conversor" />
      <label for="input-dolar">Cotação do Dólar</label>
    </span>
  </div>

  <div class="div-convensor" v-if="!conversor">
    <Button label="Limpar" @click="clear" />
    <Button label="Calcular" @click="calculate" class="button-calculate" />
  </div>

  <div v-if="conversor">
    <p class="label-result">
      Com {{ reais }} é possível comprar {{ conversor }} dólares a
      {{ dolar }} cada.
    </p>
    <Button @click="clear" label="Calcular novamente" />
  </div>

  <div></div>
</template>

<script>
export default {
  data() {
    return {
      reais: null,
      dolar: null,
      conversor: null
    };
  },
  methods: {
    calculate: function() {
      this.conversor = (this.reais / this.dolar).toFixed(2);
    },
    clear() {
      this.reais = null;
      this.dolar = null;
      this.conversor = null;
      this.result = "";
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.cifrao-logo {
  margin-right: 50px;
}
.p-float-label {
  display: inline-block !important;
}
.div conversor {
  margin-top: 2rem;
}
.button-calculate {
  margin-left: 2rem !important;
  margin-top: 2rem !important;
}
.label-result {
  font-size: 2rem;
}
</style>
