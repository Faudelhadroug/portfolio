<template>
  <div>
    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fixed: false, // ? Cache le footer si true quand il y a du contenu sur la page
    }
  },
}
</script>
