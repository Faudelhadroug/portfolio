<template>
  <v-app dark>
    <NavBar />
    <nuxt />
    <Footer />
  </v-app>
</template>

<script>
import { gsap } from 'gsap'
import NavBar from '@/components/NavBar.vue'
import Footer from '@/components/Footer.vue'
export default {
  components: {
    NavBar,
    Footer,
  },
  mounted() {
    if (this.$nuxt.$route.name === 'index') {
      const tl = gsap.timeline()
      tl.fromTo(
        '.home--first',
        { y: -screen.width * 2 },
        { y: 0, duration: 1, ease: 'expo' }
      )
      tl.fromTo('.home--second', { x: -screen.width }, { x: 0, duration: 1 }, 0)
      tl.fromTo('.home--third', { x: screen.width * 2 }, { x: 0, duration: 1 })
      tl.fromTo('.home--quatro', { y: screen.width }, { y: 0, duration: 1 }, 1)
      tl.fromTo('.home--cinco', { opacity: 0 }, { opacity: 1, duration: 10 })
      tl.fromTo(
        '.home--seis',
        { opacity: 0 },
        { opacity: 1, duration: 5 },
        '-=8.5'
      )
      tl.from('.home--cinco', 1, { scale: 1.04, repeat: -1, ease: 'boucing' })
    }
  },
}
</script>

<style>
.container {
  max-width: 100% !important;
}
body {
  margin: 0;
  height: 100%;
  overflow: hidden;
}
</style>
