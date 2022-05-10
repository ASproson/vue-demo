<template>
  <v-app>
    <v-main>
      <Header />
      <h1>Home Page</h1>
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header.vue";

export default {
  name: "App",

  components: {
    Header,
  },

  data: () => ({
    //
  }),
};
</script>

<style>
h1 {
  text-align: center;
  margin-top: 20px;
}
</style>
