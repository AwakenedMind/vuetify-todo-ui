<template>
  <div id="app">
    <v-app>
      <Navbar />
      <v-content class="mx-4 mb-4 pr-4 pl-4">
        <router-link to="/">Home</router-link>|
        <router-link to="/about">About</router-link>
        <router-view />
      </v-content>
    </v-app>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar";

export default {
  name: "App",
  components: { Navbar },
  data() {
    return {};
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
