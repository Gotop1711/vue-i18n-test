<template>
  <div id="app">
    <div class="header">
     </div>
    <router-view v-bind:guests="Guests" v-bind:companies="Companies"></router-view>
    <div class="footer">
      Thanks for looking at my Vue-i18n trial! Please feel free to contact me if you have any questions
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

export default {
  name: 'app',
  components: {
    Guests,
    Companies,
  },
  data(){
    return{
        Guests: Guests,
        Companies: Companies,
    }
  },
  beforeMount() {
        console.log("Hi there!");
  }
}
</script>

<style>
body{
  padding: 0;
  margin: 0;
  font-family: Arial, Helvetica, sans-serif
}
img{
  height: 90px;
}
a{
  color: white;
}
.header {
  height: 100px;
  background-color: #1d5dab;
  padding: 20px;
  width: 100%;
}

.footer {
  height: 100px;
  background-color: #1d5dab;
  padding: 20px;
  color: white;
  position: absolute;
  bottom: 0;
  width: 100%;
}
</style>
