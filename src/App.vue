<template>
  <div id="app">
    <div class="header">
      <img src="./assets/logo.png">
     </div>
    <router-view v-bind:guests="Guests" v-bind:companies="Companies" v-bind:templates="Templates"></router-view>
  </div>
</template>

<script>
import Guests from './jsonFiles/Guests.json';
import Companies from './jsonFiles/Companies.json';
import Templates from './jsonFiles/Templates.json';

export default {
  name: 'app',
  components: {
    Guests,
    Companies,
    Templates
  },
  data(){
    return{
        Guests: Guests,
        Companies: Companies,
        Templates: Templates,
    }
  },
  beforeMount() {
        console.log(Companies);
  }
}
</script>

<style>
#app {

}

.header {
  height: 100px;
  background-color: #1d5dab;
  padding: 20px;
}

img{
  height: 90px;
}
</style>
