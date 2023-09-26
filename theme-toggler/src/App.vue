<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png"
          transition="scale-transition"
          width="40"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>

      <v-spacer></v-spacer>

      <!-- Theme Switcher Dropdown -->
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on">
            <v-icon>mdi-palette</v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item @click="changeTheme('light')">
            <v-list-item-title>Light Theme</v-list-item-title>
          </v-list-item>
          <v-list-item @click="changeTheme('dark')">
            <v-list-item-title>Dark Theme</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main>
      Some beautiful content
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      selectedTheme: 'light', // Default theme
      themes: ['light', 'dark'], // List of available themes
    };
  },
  methods: {
    changeTheme(theme) {
      this.$vuetify.theme.dark = theme === 'dark';
    },
  },
};
</script>
