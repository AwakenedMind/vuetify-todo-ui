<template>
  <nav>
    <v-app-bar text class="grey lighten-4">
      <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="text-uppercase grey--text">
        <span class="font-weight-light">Todo</span>
        <span class="font-weight-bold">App</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>

      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn text v-on="on">
            <v-icon left>mdi-chevron-down</v-icon>
            <span>Menu</span>
          </v-btn>
        </template>
        <v-list>
          <v-list-item v-for="link in links" :key="link.text" :to="link.route">
            <v-list-item-title>{{ link.text }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>

      <v-btn text depressed>
        <span>Sign Out</span>
        <v-icon right>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app dark temporary>
      <v-layout column align-center>
        <v-flex class="mt-5">
          <v-avatar size="64">
            <v-img
              src="https://raw.githubusercontent.com/iamshaunjp/vuetify-playlist/lesson-20/todo-ninja/public/avatar-1.png"
            />
          </v-avatar>
          <p class="white--text subheading mt-1">@Ryuuu</p>
        </v-flex>

        <v-flex class="mt-4 mb-3">
          <Popup />
        </v-flex>
      </v-layout>
      <v-list>
        <v-list-item v-for="link in links" v-bind:key="link.text" router :to="link.route">
          <v-list-item-action>
            <v-icon>{{link.icon}}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title class="white--text">{{link.text}}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>

<script>
import Popup from "./Popup.vue";

export default {
  components: { Popup },
  data() {
    return {
      drawer: false,
      links: [
        { icon: "mdi-view-dashboard", text: "Dashboard", route: "/dashboard" },
        { icon: "mdi-folder", text: "My Projects", route: "/projects" },
        { icon: "mdi-team", text: "Team", route: "/team" }
      ]
    };
  }
};
</script>