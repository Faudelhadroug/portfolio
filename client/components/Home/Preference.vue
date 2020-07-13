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
        <v-col cols="1"></v-col>
        <v-col cols="5">
          <v-img class="img3 home--quatro" :src="react" alt="react logo" />
        </v-col>
        <v-col cols="5">
          <v-img class="img home--quatro" :src="nodejs" alt="nodejs logo" />
        </v-col>
        <v-col cols="1"></v-col>
      </v-row>
      <v-spacer></v-spacer>
      <v-row v-if="visible">
        <v-col cols="2"></v-col>
        <v-col class="text-center home--seis pb-4" cols="8">
          <v-btn
            :color="colorBtn"
            dark
            large
            width="175px"
            class="mouseOver"
            :outlined="!hover"
            :loading="loading"
            @mouseover="hover = true"
            @mouseleave="hover = false"
            @click="dialog = true"
            >Mes compétences</v-btn
          >
        </v-col>
        <v-col cols="2"></v-col>
      </v-row>
      <transition name="fade3">
        <!-- <div v-if="isOpen" class="modal red">
          <button @click="toggleModal">Close</button>
        </div> -->
        <v-dialog v-model="dialog" width="600px">
          <v-card>
            <span class="headline">
              <v-tabs v-model="tab" background-color="transparent" grow>
                <v-tab v-for="item in items" :key="item">
                  {{ item }}
                </v-tab>
              </v-tabs></span
            >
            <v-tabs-items v-model="tab">
              <v-tab-item v-for="(item, i) in items" :key="i">
                <v-card flat>
                  <v-card-text v-if="item === 'Front-end'">
                    <Frontend />
                  </v-card-text>
                  <v-card-text v-else-if="item === 'Back-end'">
                    <Backend />
                  </v-card-text>
                  <v-card-text v-else>
                    <Autres />
                  </v-card-text>
                </v-card>
              </v-tab-item>
            </v-tabs-items>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="green darken-1" text @click="dialog = false"
                >Fermer</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-dialog>
      </transition>
    </v-container>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tab: null,
      items: ['Front-end', 'Back-end', 'Autres'],
      nuxt: require('@/assets/preference/nuxt.svg'),
      vue: require('@/assets/preference/vue.svg'),
      react: require('@/assets/preference/react.svg'),
      nodejs: require('@/assets/preference/nodejs.svg'),
      hover: false,
      loading: false,
      visible: true,
      dialog: false,
    }
  },
  computed: {
    colorBtn() {
      return this.hover ? 'btnCallHover2' : 'btnCall2'
    },
  },
  methods: {
    toggleModal() {
      this.isOpen = !this.isOpen
    },
  },
}
</script>

<style lang="scss" scoped>
.modal {
  top: 0;
  left: 0;
  margin-left: 5%;
  position: absolute;
  width: 90%;
  height: 80%;
  padding: 10px;
  margin-top: 100px;
  border-radius: 2%;
  opacity: 0.98;
}
.mouseOver {
  transition: background-color 0.3s;
}
.fade3-enter {
  opacity: 0;
}
.fade3-enter-active,
.fade3-leave-active {
  transition: opacity 0.5s ease-out;
}

.fade3-leave-to {
  opacity: 0;
}
</style>
