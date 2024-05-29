<script setup>
import VueApexCharts from "vue3-apexcharts";

defineProps({
  type: {
    type: String,
    default: "line",
  }
})

const series = [{
  name: "Desktops",
  data: [10, 30, 25, 10, 25, 35, 22, 28, 38, 30, 22, 40]
}]
const chartOptions = {
  chart: {
    zoom: {
      enabled: false
    }
  },
  dataLabels: {
    enabled: false
  },
  stroke: {
    curve: 'smooth'
  },
  title: {
    text: 'Product Trends by Month',
    align: 'left'
  },
  grid: {
    row: {
      colors: ['#f3f3f3', 'transparent'], // takes an array which will be repeated on columns
      opacity: 0.5
    },
  },
  xaxis: {
    categories: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'],
  }
}
</script>

<template>
  <div id="workflow-chart" class="p-5 rounded">
    <VueApexCharts :type="type" height="230" :options="chartOptions" :series="series"></VueApexCharts>
  </div>
</template>

<style >
#workflow-chart {
  background-color: white;
}
</style>