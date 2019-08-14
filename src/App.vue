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
        <div class="my-2 surevey-result-slot" :key="activeSlot">
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

.surevey-result-slot ul {
  list-style: none;
  padding-left: 1rem;
}

.surevey-result-slot li {
  font-size: 1.25em;
  margin: 1rem 0;
  font-style: italic;
  color: #193D5C;
}

.survey-result-percent {
  background: #ff0;
  display: inline-block;
  min-width: 10px;
  padding: 5px 7px;
  /* font-size: 12px; */
  /* font-weight: 700; */
  line-height: 1.5;
  text-align: center;
  white-space: nowrap;
  vertical-align: middle;
  border-radius: 50%;
  border-bottom-left-radius: 0;
  border-bottom-right-radius: 0;
  color: #193D5C;
  font-style: normal;
}

.surevey-result-slot li:nth-child(1) .survey-result-percent {
  background: #A4A4A6;
  background: linear-gradient(rgba(164,164,166, 1), rgba(164,164,166, 0.5));
}
.surevey-result-slot li:nth-child(2) .survey-result-percent {
  background: #F6B5AB;
  background: linear-gradient(rgba(246,181,171, 1), rgba(246,181,171, 0.5));
}
.surevey-result-slot li:nth-child(3) .survey-result-percent {
  background: #EA7461;
  background: linear-gradient(rgba(234,116,97, 1), rgba(234,116,97, 0.5));
}
.surevey-result-slot li:nth-child(4) .survey-result-percent {
  background: #7EC9CE;
  background: linear-gradient(rgba(126,201,206, 1), rgba(126,201,206, 0.5));
}
.surevey-result-slot li:nth-child(5) .survey-result-percent {
  color: #fff;
  background: #0D4368;
  background: linear-gradient(rgba(13,67,104, 1), rgba(13,67,104, 0.5));
}
.surevey-result-slot li:nth-child(6) .survey-result-percent {
  background: #A8A9AC;
  background: linear-gradient(rgba(168,169,172, 1), rgba(168,169,172, 0.5));
}
</style>
