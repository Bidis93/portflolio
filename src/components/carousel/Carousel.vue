<template >

  <div class="carousel">
    <slot></slot>
    <button class="left-button carousel__nav carousel__prev" @click.prevent="prev"></button>
    <button class="right-button carousel__nav carousel__next" @click.prevent="next"></button>

        <br>

        <div class="carousel__pagination">
          <button v-for="n in slidesCount" @click="goto(n-1)" :class="{active: n-1 == index}"></button>
        </div>

    </div>
  </div>

</template>

<script>
export default {
  data () {
    return {
      index: 0,
      slides: [], // this.$children :pour récuperer les enfants direct de l'élément où l'on se trouve actuellement. C'est une propriété prédéfinie de Vue.js
      direction: null
    }
  },
  mounted () {
    this.slides = this.$children
    this.slides.forEach((slide, i) => {
      slide.index = i
      // Prévoir un garde-fou -> si l'index dépasse le nb d'élément total, lorsqu'on clique sur Suivant, plus rien ne s'affiche
    })
  },
  computed: {
    slidesCount () { return this.slides.length }
  },
  methods: {
    next () {
      this.index++ // ça incrémente l'index
      this.direction = 'right'
      // on créé une boucle pour revenir au premier élément lorsqu'on a fait le tour /
      // lorsqu'il est supérieur ou égal au compte total des éléments
      if (this.index >= this.slidesCount) {
        this.index = 0
      }
    },
    prev () {
      this.index--
      this.direction = 'left'
      if (this.index < 0) {
        this.index = this.slidesCount - 1
      }
    },

    goto (index) {
      this.direction = index > this.index ? 'right' : 'left'
      this.index = index
    }
  }
}
</script>

<style>

.carousel {
  position: relative;
  overflow: hidden;
}

.carousel__nav {
  position: absolute;
  top: 50%;
  margin-top: -31px;
  left: 10px;
  width: 63px;
  height: 63px;
  background-image: url(prev.png);
  background-repeat: no-repeat;
  border: none;
}

.carousel__nav.carousel__next {

  right: 10px;
  left: auto;
  background-image: url(next.png);
}

.carousel__pagination {
  position: absolute;
  bottom: 10px;
  left: 0;
  right: 0;
  text-align: center;
}

.carousel__pagination button {
  display: inline-block;
  width: 10px;
  height: 15px;
  background-color: grey;
  opacity: 0.8;
  border-radius: 10px;
  margin: 0 2px;
}

.carousel__pagination button.active {
  background-color: #fff;
}

</style>
