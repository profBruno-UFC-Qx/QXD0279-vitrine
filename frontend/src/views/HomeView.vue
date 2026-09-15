<template>
  <main>
    <AppHomeHeader />
    <AnunciosHome />
    <BannerDown />
  </main>
</template>

<script>
import AppHomeHeader from '@/components/AppHomeHeader.vue'
import AnunciosHome from '@/components/AnunciosHome.vue'
import BannerDown from '@/components/BannerDown.vue'

export default {
  name: 'HomeView',
  components: {
    AppHomeHeader,
    AnunciosHome,
    BannerDown
  }
}
</script>
