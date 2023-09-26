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
          <v-list-item
              v-for="({value, title}, i) in themes"
              :key="i"
              @click="changeTheme(value)">
            <v-list-item-title>{{title}}</v-list-item-title>
            <uil-check v-if="title === selectedTheme" size=“24” />
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main>
      <v-card class="pa-3 ma-3">Some beautiful content</v-card>
    </v-main>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      selectedTheme: 'Light',
      themes: [
          {title: 'Light', value: 'light'},
          {title: 'Dark', value: 'dark'},
      ],
    };
  },

  created() {
    this.themes.push({
      title: 'System',
      value: window.matchMedia('(prefers-color-scheme: light)').matches ? 'light' : 'dark'
    });
  },

  methods: {
    changeTheme(theme) {
      this.$vuetify.theme.dark = theme === 'dark';
    },
  },
};
</script>
