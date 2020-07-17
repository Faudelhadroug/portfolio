<template>
  <v-container>
    <form class="form">
      <v-row>
        <v-col cols="2"></v-col>
        <v-col cols="8">
          <h2>Formulaire de contact</h2>
        </v-col>
        <v-col cols="2"></v-col>
      </v-row>
      <v-row>
        <v-col cols="2"></v-col>
        <v-col
          v-if="this.$vuetify.theme.dark"
          class="card"
          :style="cardStyle"
          cols="8"
        >
          <v-text-field
            v-model="sujet"
            :counter="84"
            name="sujet"
            label="Sujet (facultatif)"
            @input="$v.sujet.$touch()"
            @blur="$v.sujet.$touch()"
          ></v-text-field>
          <v-textarea
            v-model="message"
            :error-messages="messageErrors"
            :counter="10000"
            name="message"
            label="Message"
            required
            @input="$v.message.$touch()"
            @blur="$v.message.$touch()"
          ></v-textarea>
          <v-text-field
            v-model="name"
            :error-messages="nameErrors"
            :counter="10"
            name="name"
            label="Nom"
            required
            @input="$v.name.$touch()"
            @blur="$v.name.$touch()"
          ></v-text-field>
          <v-text-field
            v-model="email"
            :error-messages="emailErrors"
            name="email"
            label="Email"
            required
            @input="$v.email.$touch()"
            @blur="$v.email.$touch()"
          ></v-text-field>
          <v-btn
            :loading="loading"
            :class="{ 'mr-4': true, error: submitErrorClass }"
            @click="submit"
            >Envoyer</v-btn
          >
          <v-btn class="btn--clear" @click="clear">Effacer</v-btn>
        </v-col>
        <v-col v-else class="card" :style="cardStyleLight" cols="8">
          <v-text-field
            v-model="sujet"
            :counter="84"
            name="sujet"
            label="Sujet (facultatif)"
            @input="$v.sujet.$touch()"
            @blur="$v.sujet.$touch()"
          ></v-text-field>
          <v-textarea
            v-model="message"
            :error-messages="messageErrors"
            :counter="10000"
            name="message"
            label="Message"
            required
            @input="$v.message.$touch()"
            @blur="$v.message.$touch()"
          ></v-textarea>
          <v-text-field
            v-model="name"
            :error-messages="nameErrors"
            :counter="10"
            name="name"
            label="Nom"
            required
            @input="$v.name.$touch()"
            @blur="$v.name.$touch()"
          ></v-text-field>
          <v-text-field
            v-model="email"
            :error-messages="emailErrors"
            name="email"
            label="Email"
            required
            @input="$v.email.$touch()"
            @blur="$v.email.$touch()"
          ></v-text-field>
          <v-btn
            :loading="loading"
            :class="{ 'mr-4': true, error: submitErrorClass }"
            @click="submit"
            >Envoyer</v-btn
          >
          <v-btn class="btn--clear" @click="clear">Effacer</v-btn>
        </v-col>
        <v-col cols="2"></v-col>
      </v-row>
      <v-row>
        <v-col cols="2" sm="4"></v-col>
        <v-col cols="8" sm="4">
          <v-alert v-show="success" type="success" width="225">
            Message envoyé
          </v-alert>
          <v-alert v-show="error" type="error" width="225">
            Erreur serveur
          </v-alert>
        </v-col>
        <v-col cols="2" sm="4"></v-col>
      </v-row>
    </form>
  </v-container>
</template>

<script>
import emailjs from 'emailjs-com'
import { validationMixin } from 'vuelidate'
import { required, maxLength, email } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
  validations: {
    name: { required, maxLength: maxLength(42) },
    email: { required, email },
    sujet: { maxLength: maxLength(84) },
    message: { required, maxLength: maxLength(10000) },
  },
  data: () => ({
    form: null,
    name: '',
    email: '',
    sujet: '',
    message: '',
    submitErrorClass: false,
    loading: false,
    success: false,
    error: false,
    cardStyle: {
      border: '2px solid white',
      borderRadius: '5px',
    },
    cardStyleLight: {
      border: '2px solid black',
      borderRadius: '5px',
    },
  }),

  computed: {
    nameErrors() {
      const errors = []
      if (!this.$v.name.$dirty) return errors
      !this.$v.name.maxLength &&
        errors.push('Votre nom ne peut pas contenir plus de 42 caractères')
      !this.$v.name.required &&
        errors.push("J'ai besoin de votre nom pour savoir qui recontacter.")
      return errors
    },
    emailErrors() {
      const errors = []
      if (!this.$v.email.$dirty) return errors
      !this.$v.email.email && errors.push("Votre email n'est pas valide")
      !this.$v.email.required &&
        errors.push(
          'Veuillez entrer votre adresse email afin que je puisse vous recontacter'
        )
      return errors
    },
    messageErrors() {
      const errors = []
      if (!this.$v.message.$dirty) return errors
      !this.$v.message.required &&
        errors.push(
          'Je vous assure que ce sera un plaisir de recevoir et lire votre message.'
        )
      return errors
    },
  },

  methods: {
    successAlert() {
      this.success = !this.success
      setTimeout(() => {
        this.success = !this.success
      }, 2500)
    },
    errorAlert() {
      this.error = !this.error
      setTimeout(() => {
        this.error = !this.error
      }, 2500)
    },
    submit() {
      this.$v.$touch()
      if (this.$v.$invalid) {
        this.submitErrorClass = true
      } else {
        this.loading = !this.loading
        this.submitErrorClass = false
        emailjs
          .sendForm(
            'gmail',
            'messageportfolio',
            '.form',
            'user_o9uKMJY12wWm6ZgmD9wDI'
          )
          .then(
            (result) => {
              this.loading = !this.loading
              this.successAlert()
            },
            () => {
              this.loading = !this.loading
              this.errorAlert()
            }
          )
      }
    },
    clear() {
      this.$v.$reset()
      this.name = ''
      this.email = ''
      this.sujet = ''
      this.message = ''
      this.submitErrorClass = false
    },
  },
  head: {
    title: 'Contact',
    meta: [
      {
        hid: 'Envoyez un message à Faudel',
        name: 'description',
        content: process.env.npm_package_description || '',
      },
    ],
  },
}
</script>

<style lang="scss" scoped>
.card {
  height: 100% !important;
}
@media (max-width: 375px) {
  .btn--clear {
    width: 70px;
    float: right;
  }
}
@media (max-width: 959px) {
  .form {
    margin-top: 10%;
    margin-bottom: 10%;
  }
}
@media (min-width: 960px) {
  .form {
    margin-top: 15%;
    margin-bottom: 10%;
  }
}

@media (min-width: 1264px) {
  .form {
    margin-top: 10%;
    margin-bottom: 10%;
  }
}
</style>
