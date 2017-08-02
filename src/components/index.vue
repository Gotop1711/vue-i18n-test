<template>
    <div class="text-compose">
        <h1>Hello!</h1>
        <div class="chooseTemplate">
            <h2>What template would you like to use?</h2>
            <div v-for="template in templates">
                <input type="radio" :id="template.name" :value="template.name" v-model="thisShit" v-on:click="fire">
                <label :for="template.name">{{template.message}}</label>
            </div>
            <span>Picked: {{ thisShit }}</span>
        </div>







        <div class="chooseGuest">
            <h2>Choose a guest</h2>
            <ul>
                <li v-for="guest in guests">
                    <button type="radio"></button>
                    {{guest.firstName}}
                </li>
            </ul>
        </div>
        <div class="chooseHotel">
            <h2>Choose your hotel</h2>
            <ul>
                <li v-for="company in companies">
                    <button type="radio"></button>
                    {{company.company}}
                </li>
            </ul>
        </div>
        <div class="finalMessage">
            <h2>Here is your final message</h2>
            <div class="displayMsg"></div>
            <button class="sendMsg">Send</button>
            <button class="editMsg">Edit</button>
            <button class="cancelMsg">Cancel</button>
        </div>
    </div>
</template>

<script>

export default {
  name: 'text-compose',
  props: ['guests', 'companies', 'templates'],
  data() {
      return{
          thisShit: '',
      }
  },
  methods: {
      fire(){
          console.log(this, this.name);
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
