<template>
    <div class="text-compose">
        <h1>Hello!</h1>
        <h2>Make your selections below to create a customized message for your guests.</h2>
        <div class="chooseWrapper">
            <h2>Please choose a template:</h2>
            <div v-for="template in templates">
                <input type="radio" :id="template.name" v-bind:value="template.message" v-model="pickedTemplate">
                <label :for="template.name">{{template.name}}</label>
            </div>
        </div>
        <div class="chooseWrapper">
            <h2>Please choose a guest:</h2>
            <div v-for="guest in guests">
                <input type="radio" :id="guest.firstName" :value="guest.firstName" v-model="pickedGuest">
                <label :for="guest.firstName">{{guest.firstName}} {{guest.lastName}}</label>
            </div>
        </div>
        <div class="chooseWrapper">
            <h2>Please choose a hotel:</h2>
            <div v-for="company in companies">
                <input type="radio" :id="company.company" :value="company.company" v-model="pickedHotel">
                <label :for="company.company">{{company.company}}</label>
            </div>
        </div>

        <div class="buttonWrapper">
            <button class="createBtn" v-on:click="create">Create your message</button>
        </div>

        <div class="finalMessage">
            <h2>Here is your final message:</h2>
            <div class="messageWrapper">
                <div v-show="!isEditing">
                    {{this.finalMsg}}
                </div>
                <div v-show="isEditing">
                    <div class='ui form'>
                        <div class='field'>
                            <textarea class="field" type='text' v-model='finalMsg' v-bind="this.finalMsg"></textarea>
                        </div>
                        <button v-on:click='hideForm'>
                            Save
                        </button>
                        </div>
                    </div>
                </div>
            </div>
            <div class="buttonWrapper">
                <button class="sendMsg" v-on:click="send">Send</button>
                <button class="editMsg" v-on:click="edit">Edit</button>
                <button class="cancelMsg" v-on:click="cancel">Cancel</button>
            </div>
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
          alert("Congrats! You sent the following message: " + this.finalMsg)
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
        this.finalMsg = "Good " + this.timeOfDay + " " + this.pickedGuest + ". This is a message from your friendly staff at " + this.pickedHotel + " :) " + this.pickedTemplate
    }
  },
  created(){
    var d = new Date();
    if(d.getHours() > 0 && d.getHours() < 12){
        this.timeOfDay = 'morning'
    }else if(d.getHours() > 12 && d.getHours() < 17){
        this.timeOfDay = 'afternoon'
    }else{
        this.timeOfDay = 'evening'
    }
  }

}
</script>

<style scoped>
h1, h2 {
  color: #86b2c7;
  margin:  20px;
}
.field{
    height: 100px;
    width: 90%;
    margin-bottom: 20px;
}
.chooseWrapper, .finalMessage{
    border: 2px solid #8eccda;
    border-radius: 5px;
    width: 400px;
    height: 200px;
    margin: 20px auto;
    padding: 10px;
    vertical-align: middle;
}
.buttonWrapper{
    margin: 0 auto;
    width: 200px;
    text-align: center;
}
</style>
