<template>
  <h1>{{joke}}</h1>
</template>

<script>
import axios from 'axios';
export default {
    created(){
        axios.get('https://api.chucknorris.io/jokes/random').then(res => {
            console.log(res.data.value);
            this.joke = res.data.value;
        });
    },
    data(){
        return{
            joke: '',

        }




    }
}
</script>

<style>

</style>
