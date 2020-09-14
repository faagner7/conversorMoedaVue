<template>
  <div id="app">
    <h1>Conversor de Moedas</h1>
    <div class="row">
      <Conversor moeda-a="USD" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="USD" />
    </div>
    <div class="row">
      <Conversor moeda-a="CAD" moeda-b="BRL" />
      <Conversor moeda-a="BRL" moeda-b="CAD" />
    </div>
    <div class="row">
      <Conversor moeda-a="BRL" moeda-b="EUR" />
      <Conversor moeda-a="EUR" moeda-b="BRL" />
    </div>
  </div>
</template>

<script>
import Conversor from "./components/Conversor.vue";
export default {
  name: "App",
  components: {
    Conversor,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#app > h1 {
  margin-bottom: 30px;
}

.row {
  display: flex;
  margin-top: 20px;
  justify-content: space-around;
}
</style>
