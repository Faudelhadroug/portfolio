<template>
  <div>
    <div class="text-lg-h6 mt-3">Language :</div>
    <v-list>
      <v-list-item
        v-for="competenceBack in competencesBack"
        :key="competenceBack"
      >
        <v-list-item-avatar>
          <v-img :src="competenceBack.image"></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title v-text="competenceBack.text"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <br />
    <div class="text-lg-h6">Framework/Bibliothèque :</div>

    <v-list>
      <v-list-item v-for="frameworkBack in frameworksBack" :key="frameworkBack">
        <v-list-item-avatar>
          <v-img :src="frameworkBack.image"></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title v-text="frameworkBack.text"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>

    <div class="text-lg-h6">Base de donnée :</div>

    <v-list>
      <v-list-item v-for="ddb in ddbs" :key="ddb">
        <v-list-item-avatar>
          <v-img :src="ddb.image"></v-img>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title v-text="ddb.text"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      competencesBack: [
        { text: 'Node.js', image: require('@/assets/logoTechno/nodejs.svg') },
        { text: 'PHP', image: require('@/assets/logoTechno/php.png') },
      ],
      frameworksBack: [
        {
          text: 'Express.js',
          image: require('@/assets/logoTechno/expressjs.png'),
        },
        { text: 'Socket', image: require('@/assets/logoTechno/socketio.png') },
        { text: 'Symfony', image: require('@/assets/logoTechno/symfony.svg') },
        { text: 'Laravel', image: require('@/assets/logoTechno/laravel.png') },
      ],
      ddbs: [
        { text: 'MySQL', image: require('@/assets/logoTechno/MySQL.svg') },
        { text: 'MongoDB', image: require('@/assets/logoTechno/mongodb.png') },
      ],
    }
  },
}
</script>

<style lang="scss" scoped></style>
