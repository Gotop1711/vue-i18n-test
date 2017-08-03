<template>
  <div id="app">
    <div class="header">
      <img src="./assets/logo.png">
     </div>
    <router-view v-bind:guests="Guests" v-bind:companies="Companies" v-bind:templates="Templates"></router-view>
    <div class="footer">
      Thanks for looking at my code challenge! Please feel free to contact me if you have any questions
      <br/>
      <a href=mailto:casie.siekman@gmail.com>casie.siekman@gmail.com</a>
      <br/>
      320.309.9433
    </div>
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
body{
  padding: 0;
  margin: 0;
}

.header {
  height: 100px;
  background-color: #1d5dab;
  padding: 20px;
}

.footer {
  height: 100px;
  background-color: #1d5dab;
  padding: 20px;
  margin-top: 30px;
  color: white;
}

img{
  height: 90px;
}

a{
  color: white;
}
</style>
