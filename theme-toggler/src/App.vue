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
      <v-container>
        <v-row align="center">
          <v-col cols="12">
            <v-select
                v-model="selectedTheme"
                :items="themes"
                label="Select Theme"
                @change="changeTheme"
            ></v-select>
          </v-col>
        </v-row>
      </v-container>

<!--      <v-btn-->
<!--        href="https://github.com/vuetifyjs/vuetify/releases/latest"-->
<!--        target="_blank"-->
<!--        text-->
<!--      >-->
<!--        <span class="mr-2">Latest Release</span>-->
<!--        <v-icon>mdi-open-in-new</v-icon>-->
<!--      </v-btn>-->
    </v-app-bar>

    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';

export default {
  name: 'App',

  components: {
    HelloWorld,
  },

  data() {
    return {
      selectedTheme: 'light', // Default theme
      themes: ['light', 'dark'], // List of available themes
    };
  },
  methods: {
    changeTheme() {
      // Use this method to switch the theme based on this.selectedTheme
      if (this.selectedTheme === 'light') {
        // Load the light theme
        this.$vuetify.theme.dark = false;
      } else {
        // Load the dark theme
        this.$vuetify.theme.dark = true;
      }
    },
  },
};
</script>
