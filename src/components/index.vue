<template>
    <div class="text-compose">
        <h1>{{ $t("message.global.good") }} {{this.timeOfDay}}!</h1>
        <h2>{{ $t("message.main.title") }}.<br/>{{ $t("message.main.subTitle") }}.</h2>

        <div class="chooseWrapper">
            <h2>{{ $t("message.choose.template") }}:</h2>
            <div v-for="template in $t('message.templates')">
                <input type="radio" :id="template.name" v-bind:value="template.message" v-model="pickedTemplate">
                <label :for="template.name">{{template.name}}</label>
            </div>
        </div>

        <div class="chooseWrapper">
            <h2>{{ $t("message.choose.guest") }}:</h2>
            <div v-for="guest in guests">
                <input type="radio" :id="guest.firstName" :value="guest.firstName" v-model="pickedGuest">
                <label :for="guest.firstName">{{guest.firstName}} {{guest.lastName}}</label>
            </div>
        </div>

        <div class="chooseWrapper">
            <h2>{{ $t("message.choose.hotel") }}:</h2>
            <div v-for="company in companies">
                <input type="radio" :id="company.company" :value="company.company" v-model="pickedHotel">
                <label :for="company.company">{{company.company}}</label>
            </div>
        </div>
        
        <br/>
        <button class="createBtn" v-on:click="create">{{ $t("message.main.create") }}</button>
        <br/>

        <div class="finalMessage">
            <h2>{{ $t("message.main.finalMsg") }}:</h2>
            <div class="messageWrapper">
                <div v-show="!isEditing">
                    {{this.finalMsg}}
                </div>
                <div v-show="isEditing">
                    <div class='ui form'>
                        <div class='field'>
                            <textarea class="field" type='text' v-model='finalMsg' value="this.finalMsg"></textarea>
                        </div>
                        <button v-on:click='saveEdits'>
                            {{ $t("message.global.saveEdits") }}
                        </button>
                        <button v-on:click='cancelEdits'>
                            {{ $t("message.global.cancelEdits") }}
                        </button>
                        </div>
                    </div>
                </div>
            </div>
            </br>
            <button class="sendMsg" v-on:click="send">{{ $t('message.global.send') }}</button>
            <button class="editMsg" v-on:click="edit">{{ $t('message.global.edit') }}</button>
            <button class="cancelMsg" v-on:click="cancel">{{ $t('message.global.cancel') }}</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'text-compose',
    props: ['guests', 'companies'],
    data() {
        return{
            pickedTemplate: '',
            pickedGuest: '',
            pickedHotel: '',
            timeOfDay: '',
            finalMsg: '',
            isEditing: false,
            friendlyMsg: this.$i18n.t('message.main.friendlyMsg'),
            good: this.$i18n.t('message.global.good')

        }
    },
    methods: {
        cancel(){
            this.pickedTemplate = '',
            this.pickedGuest = '',
            this.pickedHotel = '',
            this.finalMsg = ''
        },
        send(){
            // Here is where I would have some some of request to send the message to the guest
            alert(this.$i18n.t('message.global.congrats') + this.finalMsg)
            this.pickedTemplate = '',
            this.pickedGuest = '',
            this.pickedHotel = '',
            this.finalMsg = ''
        },
        edit(){
            this.isEditing = true;
        },
        saveEdits() {
            this.isEditing = false;
        },
        cancelEdits() {
             this.finalMsg = " " + this.timeOfDay + " " + this.pickedGuest + ". " +this.friendlyMsg + " " + this.pickedHotel + " :) " + this.pickedTemplate
             this.isEditing = false;
        },
        create(){
            if(!this.pickedGuest || !this.pickedHotel || !this.pickedTemplate ){
                alert(this.$i18n.t('message.main.alert'))
            }else{
                this.finalMsg = this.good + " " + this.timeOfDay + " " + this.pickedGuest + ". " + this.friendlyMsg + " " + this.pickedHotel + " :) " + this.pickedTemplate
            }
        }
    },
    // this fires off at page created - so we grab the correct greeting for the time of day
    created(){
        var d = new Date();
        if(d.getHours() > 0 && d.getHours() < 12){
            this.timeOfDay = this.$i18n.t('message.global.morning')
        }else if(d.getHours() > 12 && d.getHours() < 17){
            this.timeOfDay = this.$i18n.t('message.global.afternoon')
        }else{
            this.timeOfDay = this.$i18n.t('message.global.evening')
        }
    }
}
</script>

<style scoped>
h1, h2 {
  color: #86b2c7;
}
.text-compose{
    padding: 20px !important;
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
    display: inline-block;
}
</style>
