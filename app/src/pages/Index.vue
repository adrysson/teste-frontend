<template>
  <q-page class="flex flex-center">
    <div class="heading">
    </div>
    <div class="body">
      <table>
        <thead>
          <tr>
            <th>Regional</th>
            <th>Média</th>
          </tr>
        </thead>
        <!-- <tbody v-if="data.regionals">
          <tr v-for="regional in data.regionals" :key="regional.description">
            <td>{{regional.description}}</td>
            <td>{{regional.average.toFixed(2)}}%</td>
          </tr>
        </tbody> -->
      </table>
      <div class="small">
        <bar-chart :chart-data="datacollection"></bar-chart>
        <button @click="fillData()">Randomize</button>
      </div>
    </div>
  </q-page>
</template>

<style>
.small {
  max-width: 600px;
  margin:  150px auto;
}
</style>

<script>
import BarChart from '../components/BarChart.vue'

export default {
  name: 'PageIndex',
  components: {
    BarChart
  },
  data () {
    return {
      datacollection: null
    }
  },
  mounted () {
    this.fillData()
  },
  methods: {
    fillData () {
      this.$axios.get('http://localhost/teste-backend/api/v1/statistics/students/keep_studying.json')
        .then(response => {
          this.datacollection = {
            labels: response.data.regionals.map(regional => regional.description),
            datasets: [
              {
                label: 'Regionais',
                backgroundColor: '#f87979',
                data: response.data.regionals.map(regional => regional.average)
              }
            ]
          }
        })
        .catch(() => {
          this.$q.notify({
            color: 'negative',
            position: 'top',
            message: 'Não foi possível carregar os dados',
            icon: 'report_problem'
          })
        })
      // this.datacollection = {
      //   labels: [this.getRandomInt(), this.getRandomInt()],
      //   datasets: [
      //     {
      //       label: 'Data One',
      //       backgroundColor: '#f87979',
      //       data: [this.getRandomInt(), this.getRandomInt()]
      //     }, {
      //       label: 'Data One',
      //       backgroundColor: '#f87979',
      //       data: [this.getRandomInt(), this.getRandomInt()]
      //     }
      //   ]
      // }
    },
    getRandomInt () {
      return Math.floor(Math.random() * (50 - 5 + 1)) + 5
    }
  }

  // data () {
  //   return {
  //     data: {}
  //   }
  // },
  // created () {
  // this.$axios.get('http://localhost/teste-backend/api/v1/statistics/students/keep_studying.json')
  //   .then((response) => {
  //     this.data = response.data
  //     this.renderChart(this.data)
  //   })
  //   .catch(() => {
  //     this.$q.notify({
  //       color: 'negative',
  //       position: 'top',
  //       message: 'Não foi possível carregar os dados',
  //       icon: 'report_problem'
  //     })
  //   })
  // }
}
</script>
