<template lang="html">
  <div class="survey-statistic lead my-4">

    <hr>

    <div class="row d-flex align-items-center">
      <div class="col-xs-4 svg-container">
        <svg width="100%" height="100%" viewBox="0 0 42 42" class="donut img-fluid img-responsive">
          <circle class="donut-ring" cx="21" cy="21" r="15.91549430918954" fill="transparent" stroke="#ddd" stroke-width="2"></circle>

          <circle class="donut-segment" cx="21" cy="21" r="15.91549430918954" fill="transparent" :stroke="chartColor" stroke-width="3" :stroke-dasharray="dashArray" stroke-dashoffset="25"></circle>

          <text x="50%" y="50%" dominant-baseline="middle" text-anchor="middle" font-size=".4em" font-weight="bold" font-family="Arial, Helvetica, sans-serif">{{ percent }}%</text>
        </svg>
      </div>
      <div class="col-xs-8">

        <slot></slot>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    percent: {
      type: String,
      required: true
    },
    chartColor: {
      type: String,
      default: '#EA7461'
    }
  },
  computed: {
    inverse () {
      return 100 - parseInt(this.percent)
    },
    dashArray () {
      return `${this.percent} ${this.inverse}`
    }
  }
}
</script>

<style lang="css">
.survey-statistic:nth-child(even) .svg-container {
  order: 12;
}
</style>
