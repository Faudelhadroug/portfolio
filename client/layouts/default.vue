<template>
  <v-app dark>
    <NavBar />
    <nuxt />
    <Footer />
  </v-app>
</template>

<script>
import NavBar from '@/components/NavBar.vue'
import Footer from '@/components/Footer.vue'
export default {
  components: {
    NavBar,
    Footer,
  },
}
</script>

<style>
.container {
  max-width: 100%;
}
</style>
