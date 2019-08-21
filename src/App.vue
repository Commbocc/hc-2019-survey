<script>
import Statistic from './components/Statistic'
import SurveyMap from './components/SurveyMap'

export default {
  name: 'Hc2019CountywideSurvey',
  install (Vue) {
    Vue.mixin({
      components: {
        SurveyStatistic: Statistic,
        SurveyMap
      }
    })
  }
}
</script>
