<template>
  <div>
    <div class="text-lg-h6 mt-3">Language :</div>
    <v-list>
      <v-list-item
        v-for="competenceFront in competencesFront"
        :key="competenceFront"
      >
        <v-list-item-avatar>
          <v-img :src="competenceFront.image"></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title v-text="competenceFront.text"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <br />
    <div class="text-lg-h6">Framework/Bibliothèque :</div>

    <v-list>
      <v-list-item
        v-for="frameworkFront in frameworksFront"
        :key="frameworkFront"
      >
        <v-list-item-avatar>
          <v-img :src="frameworkFront.image"></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title v-text="frameworkFront.text"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      competencesFront: [
        { text: 'HTML5', image: require('@/assets/logoTechno/html5.png') },
        { text: 'CSS3', image: require('@/assets/logoTechno/css3.png') },
        { text: 'Javascript', image: require('@/assets/logoTechno/js2.png') },
      ],
      frameworksFront: [
        { text: 'Vue.js', image: require('@/assets/logoTechno/vue.svg') },
        { text: 'Vuetify', image: require('@/assets/logoTechno/vuetify.png') },
        { text: 'Nuxt.js', image: require('@/assets/logoTechno/nuxt.svg') },
        { text: 'React', image: require('@/assets/logoTechno/react.svg') },
        { text: 'Redux', image: require('@/assets/logoTechno/redux.svg') },
        { text: 'jQuery', image: require('@/assets/logoTechno/jquery.png') },
        {
          text: 'Bootstrap',
          image: require('@/assets/logoTechno/bootstrap.png'),
        },
      ],
    }
  },
}
</script>

<style lang="scss" scoped></style>
