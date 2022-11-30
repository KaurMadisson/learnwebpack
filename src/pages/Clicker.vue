<template>
    <div class="columns">
    <div class="column is-one-third has-text-centered">

         <b>{{displayCookies}} cookies</b>
            <br>
            <b>{{displayCps}} Cookies per second</b>
            <br>
            <b>{{displayCpc}} cookies per click</b>
            <br>
            <br>
        

        <img @click="cookieClick()" :class="{'click' :clickClass}" src ="https://www.freeiconspng.com/uploads/download-biscuit-cookie-monster-clipart-24.png">
        </div>
        <div class="cps">
            <button @click="upgrade(0.1, 10)" class="button is-primary" :disabled="cookies<=10"> Buy 0.1 cps for 10 cookies </button>
            <br>
            <br>
            <button @click="upgrade(1, 100)" class="button is-primary" :disabled="cookies<=100"> Buy 1 cps for 100 cookies </button>
            <br>
            <br>
            <button @click="upgrade(10, 1000)" class="button is-primary" :disabled="cookies<=1000"> Buy 10 cps for 1000 cookies </button>
            <br>
            <br>
            <button @click="upgrade(100, 10000)" class="button is-primary" :disabled="cookies<=10000"> Buy 100 cps for 10000 cookies </button>
            <br>
            <br>
            <button @click="upgrade(1000, 100000)" class="button is-primary" :disabled="cookies<=100000"> Buy 1000 cps for 100000 cookies </button>
            <br>
            <br>
<div class="column is-one-third">
                <div class="cpc">
                    <br>
                    200 clicks to get a Golden Cookie
                </div><br>
        




            <img @click="cookieClick()" :class="{'click' :clickClass}" src ="https://tr.rbxcdn.com/beca9d82f693d83707ff5a17fa82ebfb/420/420/Image/Png">
        </div>
        <div class="gc">

            
          
            




</div>

            <button1 @click="gc()" class="button is-primary" :disabled="cookies<=0">  Golden Cookie</button1>
            <br>
            <br>
            <button @click="upgrade2(1, 10), gcookie()" class="button is-primary" :disabled="cookies<=10"> Buy 0.1 cpc for 10 cookies </button>
            <br>
            <br>
            <button @click="upgrade2(10, 1000)" class="button is-primary" :disabled="cookies<=100"> Buy 1 cpc for 100 cookies </button>
            <br>
            <br>
            <button @click="upgrade2(100, 10000)" class="button is-primary" :disabled="cookies<=1000"> Buy 10 cpc for 1000 cookies </button>
            <br>
            <br>
            <button @click="upgrade2(1000, 100000)" class="button is-primary" :disabled="cookies<=10000"> Buy 100 cpc for 10000 cookies </button>
            <br>
            <br>
            <button @click="upgrade2(10000, 1000000)" class="button is-primary" :disabled="cookies<=100000"> Buy 1000 cpc for 100000 cookies </button>
            <br>
            <br>


            
        </div>
        </div>


</template>

<script>

export default {
    created(){
        setInterval(()=>{
            this.cookies += this.cps;
            this.cookies = parseFloat (this.cookies.toFixed(1));
        }, 1000);
    },

  data(){
      return{
       
          clickClass: false,
          cookies:0,
          cps: 0,
          cpc: 1,
          upgrade3Disabled: true,
          a: [0],
          cC: 0,

        }
    },

    
       computed: {
        displayCookies(){
            return parseFloat(this.cookies.toFixed(1));
        },
        displayCps(){
            return parseFloat(this.cps.toFixed(1));
        },
        displayCpc(){
            return parseFloat(this.cpc.toFixed(1));
        },

        

    


},




    methods: {
        cookieClick(){
            this.cookies += this.cpc;
            this.cC++;
            clickClass = true;
            setTimeout(()=> {
                this.clickClass = false;

            }, 13000);
        },
        
        upgrade(cps, cost){
            if(this.cookies >= cost){
                this.cookies -= cost;
                this.cps += cost;

            }
        },
        upgrade2(cpc, cost){
            if(this.cookies >= cost){
                this.cookies -= cost;
                this.cpc += cost;

            }
        },
            gc(){
                if(this.a[0]==0){
                this.cookies+=500
                this.a[0]+=1
                }
                if(this.cC==200){
                    this.cC=0;
                    this.a[0]=0;
                }
        },

    

        
    },
    }
    



</script>


<style scoped>
    img.click {
        transform: scale (0.9);
    }
    .button {
       font-family: 'verdana';
       background-color: blue;
       
    }
    

</style>

<style>

</style>