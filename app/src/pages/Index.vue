<template>
  <q-page v-if="Object.entries(data).length">
    <div class="heading grid" align="center">
        <h1>Relatório</h1>
        <legend>Ex-alunos de SENAI que continuam estudando</legend>
    </div>
    <div class="body" align="center">
        <bar-chart :width="800" :height="300" :chart-data="datacollection"></bar-chart>
    </div>
    <div class="footer" align="center">
      <p class="national">Nacional: {{data ? data.national.toFixed(2) : ''}}</p>
    </div>
  </q-page>
</template>

<style>
.heading h1 {
  font-size: 4rem;
  font-weight: bold;
  margin: 0px;
}

.heading {
  margin: 50px 0px 20px 0px;
}

.footer {
  margin: 25px 0px 0px 0px;

}
.footer .national{
  color: red;
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
      datacollection: null,
      data: {}
    }
  },
  mounted () {
    this.$q.loading.show()
    this.$axios.get(`${process.env.API}/v1/statistics/students/keep_studying.json`)
      .then(response => {
        this.data = response.data
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
      .then(() => {
        this.$q.loading.hide()
      })
  },
  methods: {}
}
</script>
