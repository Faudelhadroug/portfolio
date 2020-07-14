<template>
  <div>
    <div class="text-lg-h6 mt-3">Méthodologies :</div>
    <v-list>
      <v-list-item v-for="methodologie in methodologies" :key="methodologie">
        <v-list-item-content>
          <v-list-item-title v-text="methodologie"></v-list-item-title>
        </v-list-item-content>

        <v-list-item-avatar>
          <v-img></v-img>
        </v-list-item-avatar>
      </v-list-item>
    </v-list>
    <br />
    <div class="text-lg-h6">Autres :</div>

    <v-list>
      <v-list-item v-for="autre in autres" :key="autre">
        <!-- <v-list-item-avatar>
        <v-img>test</v-img>
      </v-list-item-avatar> -->
        <v-list-item-content>
          <v-list-item-title v-text="autre"></v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </div>
</template>

<script>
export default {
  data() {
    return {
      methodologies: ['Agile'],
      autres: [
        'Trello',
        'Git',
        'Github',
        'Gitlab',
        'Twig',
        'Blade',
        'Sony Vegas Pro',
        'Adobe Photoshop',
        'Adobe InDesign',
        'Adobe Illustrator',
        'Adobe After Effect',
        'Adobe Premiere Pro',
        'Adobe Color',
      ],
    }
  },
}
</script>

<style lang="scss" scoped></style>
