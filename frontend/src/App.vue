<template>
  <AppNavbar />
  <RouterView class="conteudo-principal" />
  <FooterBar />
</template>

<script>
import AppNavbar from './components/AppNavbar.vue';
import FooterBar from './components/FooterBar.vue';

export default {
  name: 'App',
  components: {
    AppNavbar,
    FooterBar
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 10px;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.conteudo-principal {
  flex: 1;
  width: 100%;
}

body {
  margin: 0;
  background-color: #f8fafc;
}

#app > .footer {
  margin-top: auto;
}
</style>
