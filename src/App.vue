<template>
  <main id="app">
    <div class="container">
      <Operacoes />
    </div>
  </main>
</template>

<script>
import Operacoes from "./components/Operacoes.vue";


export default {
  name: "App",

  components: {
    Operacoes,
  },
};
</script>

