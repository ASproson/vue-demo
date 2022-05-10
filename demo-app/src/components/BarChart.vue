<template>
  <div id="chart-wrapper">
    <v-card>
      <Bar :chart-data="chartDataLocal" style="padding: 15px" />
    </v-card>
  </div>
</template>

<script>
import { Bar } from "vue-chartjs";
import {
  Chart as ChartJS,
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale,
} from "chart.js";

ChartJS.register(
  Title,
  Tooltip,
  Legend,
  BarElement,
  CategoryScale,
  LinearScale
);

const chartTitle = "Months";
const chartLabels = ["January", "February", "March"];
const chartLabelsTwo = ["March", "April", "May"];
const dataForChart = [40, 20, 12];

export default {
  name: "BarChartLocalData",
  components: { Bar },
  data: () => ({
    loaded: false,
    chartDataAPI: null,
  }),
  async mounted() {
    this.loaded = false;
    try {
      const { apiData } = await fetch("/api/apiData");
      this.chartDataAPI = apiData;
      this.loaded = true;
    } catch (e) {
      console.error(e);
    }
  },
  data() {
    return {
      chartDataLocal: {
        labels: chartLabels,
        datasets: [
          {
            label: chartTitle,
            data: dataForChart,
            backgroundColor: [
              "rgba(255, 99, 132, 0.2)",
              "rgba(54, 162, 235, 0.2)",
              "rgba(255, 206, 86, 0.2)",
            ],
            borderColor: [
              "rgba(255, 99, 132, 1)",
              "rgba(54, 162, 235, 1)",
              "rgba(255, 206, 86, 1)",
            ],
            borderWidth: 1,
          },
        ],
      },
      chartDataLocalTwo: {
        labels: chartLabelsTwo,
        datasets: [
          {
            label: chartTitle,
            data: dataForChart,
            backgroundColor: [
              "rgba(255, 99, 132, 0.2)",
              "rgba(54, 162, 235, 0.2)",
              "rgba(255, 206, 86, 0.2)",
            ],
            borderColor: [
              "rgba(255, 99, 132, 1)",
              "rgba(54, 162, 235, 1)",
              "rgba(255, 206, 86, 1)",
            ],
            borderWidth: 1,
          },
        ],
      },
    };
  },
};
</script>

<style scoped>
#chart-wrapper {
  max-height: 400px;
  max-width: 400px;
  margin: 0 auto;
  margin-top: 15px;
}
</style>
