<template>
    <div class="text-compose">
        <h1>Hello!</h1>
        <div class="chooseTemplate">
            <h2>What template would you like to use?</h2>
            <div v-for="template in templates">
                <input type="radio" :id="template.name" v-bind:value="template.name" v-model="pickedTemplate">
                <label :for="template.name">{{template.message}}</label>
            </div>
            <span>Picked: {{ pickedTemplate }}</span>
        </div>

        <div class="chooseGuest">
            <h2>Choose a guest</h2>
            <div v-for="guest in guests">
                <input type="radio" :id="guest.firstName" :value="guest.firstName" v-model="pickedGuest">
                <label :for="guest.firstName">{{guest.firstName}}</label>
            </div>
            <span>Picked: {{ pickedGuest }}</span>
        </div>

        <div class="chooseHotel">
            <h2>Choose your hotel</h2>
            <div v-for="company in companies">
                <input type="radio" :id="company.company" :value="company.company" v-model="pickedHotel">
                <label :for="company.company">{{company.company}}</label>
            </div>
            <span>Picked: {{ pickedHotel }}</span>
        </div>

        <div class="finalMessage">
            <h2>Here is your final message</h2>
            <div v-if="this.pickedHotel && this.pickedGuest && this.pickedTemplate">
            {{this.pickedTemplate}} {{this.pickedGuest}} {{this.pickedHotel}}
            </div>
            <div v-else>Finish picking</div>
            
            <div class="displayMsg"></div>
            <button class="sendMsg" v-on:click="fire">Send</button>
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
          pickedTemplate: '',
          pickedGuest: '',
          pickedHotel: '',
      }
  },
  methods: {
      fire(){
          console.log(this.pickedTemplate, this.pickedGuest, this.pickedHotel);
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
