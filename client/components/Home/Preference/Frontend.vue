<template>
  <div>
    <div class="text-lg-h6 mt-3">Language :</div>
    <v-list>
      <v-list-item
        v-for="competenceFront in competencesFront"
        :key="competenceFront"
      >
        <v-list-item-content>
          <v-list-item-title v-text="competenceFront"></v-list-item-title>
        </v-list-item-content>

        <v-list-item-avatar>
          <v-img></v-img>
        </v-list-item-avatar>
      </v-list-item>
    </v-list>
    <br />
    <div class="text-lg-h6">Framework/Bibliothèque :</div>

    <v-list>
      <v-list-item
        v-for="frameworkFront in frameworksFront"
        :key="frameworkFront"
      >
        <!-- <v-list-item-avatar>
        <v-img>test</v-img>
      </v-list-item-avatar> -->
        <v-list-item-content>
          <v-list-item-title v-text="frameworkFront"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      competencesFront: ['HTML 5', 'CSS3', 'Javascript'],
      frameworksFront: [
        'Vue.js',
        'Vuetify',
        'Nuxt.js',
        'React',
        'Redux',
        'jQuery',
        'Bootstrap',
      ],
    }
  },
}
</script>

<style lang="scss" scoped></style>
