<template>
  <v-app>
    <v-main>
      <Header />
      <h1>Home Page</h1>
      <div id="chart-container">
        <BarChart />
        <BarChart />
        <BarChart />
      </div>
    </v-main>
  </v-app>
</template>

<script>
import Header from "./components/Header.vue";
import BarChart from "./components/BarChart.vue";

export default {
  name: "App",

  components: {
    Header,
    BarChart,
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

#chart-container {
  display: flex;
}
</style>
