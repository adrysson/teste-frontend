<template>
  <q-page class="flex flex-center">
    <div class="heading">
    </div>
    <div class="body">
      <bar-chart :width="600" :height="300" :chart-data="datacollection"></bar-chart>
    </div>
  </q-page>
</template>

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
    this.$axios.get('http://localhost/teste-backend/api/v1/statistics/students/keep_studying.json')
      .then(response => {
        this.datacollection = {
          labels: response.data.regionals.map(regional => regional.description),
          datasets: [
            {
              label: 'Regionais',
              backgroundColor: '#f87979',
              data: response.data.regionals.map(regional => regional.average.toFixed(2))
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
  },
  methods: {}
}
</script>
