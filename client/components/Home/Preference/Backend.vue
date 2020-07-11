<template>
  <div>
    <div class="text-lg-h6 mt-3">Language :</div>
    <v-list>
      <v-list-item
        v-for="competenceBack in competencesBack"
        :key="competenceBack"
      >
        <v-list-item-content>
          <v-list-item-title v-text="competenceBack"></v-list-item-title>
        </v-list-item-content>

        <v-list-item-avatar>
          <v-img></v-img>
        </v-list-item-avatar>
      </v-list-item>
    </v-list>
    <br />
    <div class="text-lg-h6">Framework/Bibliothèque :</div>

    <v-list>
      <v-list-item v-for="frameworkBack in frameworksBack" :key="frameworkBack">
        <!-- <v-list-item-avatar>
        <v-img>test</v-img>
      </v-list-item-avatar> -->
        <v-list-item-content>
          <v-list-item-title v-text="frameworkBack"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>

    <div class="text-lg-h6">Base de donnée :</div>

    <v-list>
      <v-list-item v-for="ddb in ddbs" :key="ddb">
        <!-- <v-list-item-avatar>
        <v-img>test</v-img>
      </v-list-item-avatar> -->
        <v-list-item-content>
          <v-list-item-title v-text="ddb"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      competencesBack: ['Node.js', 'PHP'],
      frameworksBack: ['Express.js', 'Socket.io', 'Symfony', 'Laravel'],
      ddbs: ['MySQL', 'MongoDB'],
    }
  },
}
</script>

<style lang="scss" scoped></style>
