<template>
    <div class="text-compose">
        <h1>Hello!</h1>
        <div class="chooseTemplate">
            <h2>Please choose a template:</h2>
            <div v-for="template in templates">
                <input type="radio" :id="template.name" v-bind:value="template.message" v-model="pickedTemplate">
                <label :for="template.name">{{template.message}}</label>
            </div>
        </div>

        <div class="chooseGuest">
            <h2>Please choose a guest:</h2>
            <div v-for="guest in guests">
                <input type="radio" :id="guest.firstName" :value="guest.firstName" v-model="pickedGuest">
                <label :for="guest.firstName">{{guest.firstName}}</label>
            </div>
        </div>

        <div class="chooseHotel">
            <h2>Please choose a hotel:</h2>
            <div v-for="company in companies">
                <input type="radio" :id="company.company" :value="company.company" v-model="pickedHotel">
                <label :for="company.company">{{company.company}}</label>
            </div>
        </div>

        <button v-on:click="create">Create your message</button>


        <div class="finalMessage">
            <h2>Here is your final message:</h2>
            <div class="messageWrapper">
                <div v-show="!isEditing">
                    {{this.finalMsg}}
                </div>
                
                <div v-show="isEditing">
                    <div class='ui form'>
                        <div class='field'>
                            <input class="field" type='text' v-model='finalMsg' v-bind="this.finalMsg">
                        </div>
                        <button class='ui basic blue button' v-on:click='hideForm'>
                            Close X
                        </button>
                        </div>
                    </div>
                </div>
            
            <div class="displayMsg"></div>
            <button class="sendMsg" v-on:click="send">Send</button>
            <button class="editMsg" v-on:click="edit">Edit</button>
            <button class="cancelMsg" v-on:click="cancel">Cancel</button>
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
          timeOfDay: '',
          finalMsg: '',
          isEditing: false,
      }
  },
  methods: {
      fire(){
          console.log(this.pickedTemplate, this.pickedGuest, this.pickedHotel);
      },
      cancel(){
          this.pickedTemplate = '',
          this.pickedGuest = '',
          this.pickedHotel = ''
      },
      send(){
          console.log("send")
          alert("Congrats! You sent send the following message: " + this.finalMsg)
      },
      edit(){
          this.isEditing = true;
          console.log("edit")
      },
      hideForm() {
        this.isEditing = false;
        console.log(this.finalMsg)
    },
    create(){
        this.finalMsg = "Good " + this.timeOfDay + " " + this.pickedGuest + ", This is a message from your friendly staff at " + this.pickedHotel + " :)" + this.pickedTemplate
    }
  },
  created(){
    var d = new Date();
    d.getHours();
    d.getMinutes(); 
    d.getSeconds();
    console.log(d)
    console.log(d.getHours())
    if(d.getHours > 0 && d.getHours < 12){
        this.timeOfDay = 'morning'
    }else if(d.getHours > 12 && d.getHours < 17){
        this.timeOfDay = 'afternoon'
    }else{
        this.timeOfDay = 'evening'
    }
    console.log(this.timeOfDay)
  }

}
</script>

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

.field{
    height: 200px;
    width: 400px;
}
</style>
