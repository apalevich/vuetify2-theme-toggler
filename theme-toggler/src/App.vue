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
              v-for="(theme, i) in themes"
              :key="i"
              @click="changeTheme(theme)">
            <v-list-item-title>{{theme.title}}</v-list-item-title>
            <uil-check v-if="theme.title === selectedTheme" size=“24” />
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main>
      <v-card class="pa-3 ma-3">Some beautiful content</v-card>
    </v-main>

    <!--  Snackbar  -->
    <v-snackbar
        v-model="snackbar"
    >
      Your theme changed to the {{ selectedTheme }}

      <template v-slot:action="{ attrs }">
        <v-btn
            color="red"
            text
            v-bind="attrs"
            @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </v-app>
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      selectedTheme: localStorage.getItem('selectedTheme') || 'Light',
      themes: [
          {title: 'Light', value: 'light'},
          {title: 'Dark', value: 'dark'},
      ],
      snackbar: false,
      text: `Hello, I'm a snackbar`,
    };
  },

  created() {
    this.themes.push({
      title: 'System',
      value: window.matchMedia('(prefers-color-scheme: light)').matches ? 'light' : 'dark'
    });
    this.$vuetify.theme.dark = this.themes.find(el => el.title=='Light').value;
  },

  methods: {
    changeTheme({title, value}) {
      this.$vuetify.theme.dark = value === 'dark';
      this.selectedTheme = title;
      this.snackbar = true;

      localStorage.setItem('selectedTheme', title);
    },
  },
};
</script>
