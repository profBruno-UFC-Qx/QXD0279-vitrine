<template>
  
  
  <AppNavbar> </AppNavbar>

  <AppHomeHeader />

  <AnunciosHome />

  <BannerDown />
  
  <footer class="footer">
    <FooterBar> </FooterBar>
  </footer>
  
</template>

<script>
import AppNavbar from './components/AppNavbar.vue';
import FooterBar from './components/FooterBar.vue';
import AppHomeHeader from './components/AppHomeHeader.vue';
import AnunciosHome from './components/AnunciosHome.vue';
import BannerDown from './components/BannerDown.vue';

export default {
  name: 'App',
  components: {
    AppNavbar,
    FooterBar,
    AppHomeHeader,
    AnunciosHome,
    BannerDown
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

.footer {
  display: flex;
  align-items: flex-end;
  margin-top: auto;
}
</style>
