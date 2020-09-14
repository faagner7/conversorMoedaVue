<template>
  <div class="conversor">
    <h2>{{moedaA}} Para {{moedaB}}</h2>
    <input type="text" v-model="moedaA_value" v-bind:placeholder="moedaA" />
    <input type="button" value="Converter" v-on:click="converter" />
    <h2 v-if="moedaB_value">Convertido: {{moedaB_value}}</h2>
    <h4 v-if="cotacaoAtual">Cotação atual: {{cotacaoAtual}}</h4>
  </div>
</template>

<script>
export default {
  name: "Conversor",
  props: ["moedaA", "moedaB"],
  data() {
    return {
      moedaA_value: "",
      moedaB_value: "",
      cotacaoAtual: "",
    };
  },
  methods: {
    converter() {
      const de_para = this.moedaA + "_" + this.moedaB;
      console.log(de_para);
      const url =
        "https://free.currconv.com/api/v7/convert?q=" +
        de_para +
        "&compact=ultra&apiKey=1934329ac124eb701bcc";

      fetch(url)
        .then((response) => {
          return response.json();
        })
        .then((response) => {
          const cotacao = response[de_para];
          this.cotacaoAtual = parseFloat(cotacao).toFixed(2);
          this.moedaB_value = parseFloat(cotacao * this.moedaA_value).toFixed(
            2
          );
        });
    },
  },
};
</script>

<style scoped>
.conversor {
  max-width: 300px;
  height: auto;
  padding: 20px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  min-height: 150px;
}
.conversor > input {
  margin-right: 10px;
}
</style>