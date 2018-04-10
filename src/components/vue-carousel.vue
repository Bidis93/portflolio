<template>
   <div>
     <carousel>
        <slide>
           <img v-bind:src="img">
       </slide>
      <slide>
          <img v-bind:src="img2">
      </slide>
    </carousel>
</div>
</template>

<script>
export default{
  data () {
   return {
        img: require('../assets/as-de-pique.png')
        img2: require('../assets/bioforceenergia.png')
      }
    }
 }
</script>

<style>
/*#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
*/
</style>
