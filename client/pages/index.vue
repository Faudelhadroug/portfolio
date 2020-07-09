<template>
  <div>
    <Home />
  </div>
</template>

<script>
import Home from '@/components/Home/Home.vue'
export default {
  components: {
    Home,
  },
  methods: {
    sendEmail() {
      alert('test')
    },
  },
}
</script>
