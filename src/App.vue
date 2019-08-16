<script>
import Statistic from './components/Statistic'

export default {
  name: 'Hc2019CountywideSurvey',
  install (Vue) {
    Vue.mixin({
      components: {
        SurveyStatistic: Statistic
      }
    })
  }
}
</script>
