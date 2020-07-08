<template>
  <div>
    <v-container>
      <v-row>
        <v-col cols="12">
          <h3 class="text-center home--third ml-3 mb-10">
            Mes préférences
          </h3>
        </v-col>
      </v-row>
    </v-container>
    <v-container>
      <v-row>
        <v-col cols="1"></v-col>
        <v-col cols="5">
          <v-img class="img home--quatro" :src="nuxt" alt="nuxt logo" />
        </v-col>
        <v-col cols="5">
          <v-img class="home--quatro" :src="vue" alt="vue logo" />
        </v-col>
        <v-col cols="1"></v-col>
      </v-row>
      <v-row>
        <v-col cols="6">
          <v-img class="img3 home--quatro" :src="react" alt="react logo" />
        </v-col>
        <v-col cols="6">
          <v-img class="img home--quatro" :src="nodejs" alt="nodejs logo" />
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import nuxtPNG from '@/assets/nuxt.svg'
import vuePNG from '@/assets/vue.svg'
import reactPNG from '@/assets/react.svg'
import nodejsPNG from '@/assets/nodejs.svg'
export default {
  data() {
    return {
      nuxt: nuxtPNG,
      vue: vuePNG,
      react: reactPNG,
      nodejs: nodejsPNG,
    }
  },
}
</script>

<style lang="scss" scoped></style>
