<template>
  <v-container>
    <div class="small">
    <bar-chart :chartData="datacollection" :options="options"/>
    <button @click="fillData()">Randomize</button>
    </div>
  </v-container>
</template>

<script>
import BarChart from './BarChart.vue'
  export default {
    name: 'HelloWorld',
    components: {
      BarChart
    },
    data () {
      return {
        datacollection: {labels:[],datasets:[]},
        options: {
          responsive: true,
          maintainAspectRatio: false
        }
      }
    },
    mounted () {
       this.fillData()
    },
    methods: {
      fillData () {
        this.datacollection = {
          labels: [this.getRandomInt()],
          datasets: [
            {
              label: 'Data One',
              backgroundColor: '#f87946',
              data: [this.getRandomInt(), this.getRandomInt()]
            }, {
              label: 'Data Two',
              backgroundColor: '#f87979',
              data: [this.getRandomInt(), this.getRandomInt()]
            }
          ]
        }
        console.log(this.datacollection)
      },
      getRandomInt () {
        return Math.floor(Math.random() * (50 - 5 + 1)) + 5
      }
    }
  }
</script>
<style>
  .small {
    max-width: 600px;
    margin:  150px auto;
  }
</style>
