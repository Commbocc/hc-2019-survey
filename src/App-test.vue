<template>
  <main id="hc-main" class="d-flex flex-column">

    <header>
      <nav is="hc-navbar" logo-href="./" class="v-card"></nav>
    </header>

    <section class="">

      <div class="row no-gutters">
        <div class="col-lg-4 order-lg-12">

          <Map />

        </div>
        <div class="col-lg-8">

          <div class="py-5">
            <div class="container">

              <!-- <img alt="Vue logo" src="./assets/logo.png"> -->

              <HelloWorld msg="Welcome to Your Vue.js App"/>

              <figure class="bg-light p-3 text-muted small">
                <figcaption class="mb-3">
                  The Board received a special appearance by Robert Allen, Vice President, HCP Associates Inc., who presented a preliminary report on the Citizens' Feedback Survey.
                </figcaption>
                <div class="embed-responsive embed-responsive-16by9">
                  <iframe class="embed-responsive-item" src="https://www.youtube.com/embed/BKSVkanB8r4?start=9206&rel=0" allowfullscreen></iframe>
                </div>
              </figure>

            </div>
          </div>

          <div is="hc-parallax" gradient="info" :height="250" src="http://www.cansolveckd.ca/wp-content/uploads/2018/05/pe-survey-highlights.jpg">
            <h2 class="text-center font-weight-bold text-shadow m-0">
              <small class="d-block">
                Hillsborough County
              </small>
              Citizens' Feedback Survey
            </h2>
          </div>

          <div class="py-5">
            <div class="container">

              <HelloWorld msg="Welcome to Your Vue.js App"/>

            </div>
          </div>

        </div>
      </div>
    </section>


    <footer>
      <nav is="hc-footer"></nav>
    </footer>

  </main>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Map from './components/Map'

export default {
  name: 'app',
  components: {
    HelloWorld, Map
  }
}
</script>

<style lang="scss" src="./assets/main.scss"></style>
