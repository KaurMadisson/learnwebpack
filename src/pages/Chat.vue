<template>
    <div v-if="!isNameSet">
        <input type="text" class="input" v-model="name" @keydown.enter="join()" placeholder="Name">
    </div>
    <div v-else>  
        <input type="text" class="input" v-model="message" @keydown.enter="send()" placeholder="Message">
        <div class="columns" v-for="(msg,index) in messages" :key="index">
            <div class="column is-half is-flex" :class="{'is-justify-content-end is-offset-half': msg.isMe}">
                <div class="notification m-2 p-2 is-size-4" :class="{'is-info': !msg.isMe, 'is-primary': msg.isMe}">
                    {{msg.name}}: <br>
                    {{msg.text}}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    mounted(){
        this.ws = new WebSocket('ws://localhost:8080');
        // Listen for messages
        this.ws.addEventListener('message', this.onMessage);
    },
    data(){
        return {
            message: '',
            ws: null,
            messages: [
                // {text:'asdasd', isMe: true},
                // {text:'gdfgfgf', isMe: false},
                // {text:'vcvcvc', isMe: true},
            ],
            isNameSet: false,
            name: ''
        }
    },
    methods: {
        sendJson(type, data){
            this.ws.send(JSON.stringify({type:type, data: data}));
        },
        send(){
           this.sendJson('message', this.message);
           this.messages.push({text:this.message, isMe: true, name: this.name});
           this.message = '';
           
        },
        join(){
            this.sendJson('name', this.name);
            this.isNameSet = true;
        },
        onMessage(event) {
       
            let data = JSON.parse(event.data);
            console.log(data);
            this.messages.push(data.data);
        }
    }
}
</script>

<style scoped>
    .notification {
        width: fit-content;
        overflow-wrap: anywhere;
    }
</style>