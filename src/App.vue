<template>

  <div class="container">

    <b-navbar toggleable="md" type="dark" variant="info">

      <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

      <b-navbar-brand class="colorFont" style= "color: black">Portfolio</b-navbar-brand>
      <b-navbar-brand class="colorFont" style="color: black">Florian Labare</b-navbar-brand>

      <b-collapse is-nav id="nav_collapse">

        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">

          <b-nav-form>
            <b-form-input size="sm" class="mr-sm-2" type="text" placeholder="Search"/>
            <b-button size="sm" class="my-2 my-sm-0" type="submit">Search</b-button>
          </b-nav-form>

          <b-nav-item-dropdown text="Lang" right>
            <b-dropdown-item href="#">EN</b-dropdown-item>
            <b-dropdown-item href="#">ES</b-dropdown-item>
            <b-dropdown-item href="#">RU</b-dropdown-item>
            <b-dropdown-item href="#">FA</b-dropdown-item>
          </b-nav-item-dropdown>

          <b-nav-item-dropdown right>
            <!-- Using button-content slot -->
            <template slot="button-content">
              <em>User</em>
            </template>
            <b-dropdown-item href="#">Profile</b-dropdown-item>
            <b-dropdown-item href="#">Signout</b-dropdown-item>
          </b-nav-item-dropdown>
        </b-navbar-nav>

      </b-collapse>
    </b-navbar>
    <carousel class="carouselStyle">

      <carousel-slide>
           <img v-bind:src="img"height="380" width="auto" >
      </carousel-slide>

      <carousel-slide>
          <img :src="img2" height="380" width="auto">
      </carousel-slide>

      <carousel-slide>
          <img :src="img3" height="380" width="auto">
      </carousel-slide>

    </carousel>

  </div>
</template>

<script>
import Vue from 'vue'
import BootstrapVue from 'bootstrap-vue'

import 'bootstrap/dist/css/bootstrap.css'
import 'bootstrap-vue/dist/bootstrap-vue.css'

import Carousel from './components/carousel/Carousel'
import CarouselSlide from './components/carousel/CarouselSlide'

Vue.use(BootstrapVue)

export default {
  components: {
    Carousel,
    CarouselSlide

  },
  data () {
    return {
      img: require('./assets/as-pique.png'),
      img2: require('./assets/bioforce.png'),
      img3: require('./assets/crocoA3.png')
      // imgPrev: require ('.assets/prev.png')
    }
  }
}
</script>

<style>

.colorFont {
  font-family: helvetica, black;
}

.carouselStyle {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.bg-info {
    background-color: lightgrey !important;
    border: solid, 1px, black;
}

.carouselStyle {
    margin-top: 30px;
    padding-bottom: 20px;
}

</style>
