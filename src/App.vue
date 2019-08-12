<template lang="html">
  <div class="row">

    <div class="col-lg-7">
      <SurveyMap class="mb-3" />
    </div>

    <div class="col-lg-5">

      <!-- Nav tabs -->
      <ul class="nav nav-tabs" role="tablist">
        <li role="presentation" :class="isTabActive('average')">
          <a href="#average" @click="activeSlot = 'average'" class="px-3 py-2">Average</a>
        </li>
        <li role="presentation" :class="isTabActive('district1')">
          <a href="#district1" @click="activeSlot = 'district1'" class="px-3 py-2">District 1</a>
        </li>
        <li role="presentation" :class="isTabActive('district2')">
          <a href="#district2" @click="activeSlot = 'district2'" class="px-3 py-2">2</a>
        </li>
        <li role="presentation" :class="isTabActive('district3')">
          <a href="#district3" @click="activeSlot = 'district3'" class="px-3 py-2">3</a>
        </li>
        <li role="presentation" :class="isTabActive('district4')">
          <a href="#district4" @click="activeSlot = 'district4'" class="px-3 py-2">4</a>
        </li>
      </ul>

      <transition name="fade" mode="out-in">
        <div class="my-2" :key="activeSlot">
          <slot :name="activeSlot"></slot>
        </div>
      </transition>

    </div>

  </div>
</template>

<script>
import SurveyMap from './components/SurveyMap'

export default {
  name: 'Hc2019CountywideSurvey',
  install (Vue) {
    Vue.mixin({
      components: {
        Hc2019CountywideSurvey: this
      }
    })
  },
  components: {
    SurveyMap
  },
  data: () => ({
    activeSlot: 'average'
  }),
  methods: {
    isTabActive (tab) {
      return tab == this.activeSlot ? 'active' : null
    }
  }
}
</script>

<style media="screen">
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
