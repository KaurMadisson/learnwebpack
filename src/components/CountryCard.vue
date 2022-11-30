<template>
    <button class="button is-primary" @click="activeField='Confirmed'">Confirmed</button>
    <button class="button is-primary" @click="activeField='Deaths'">Deaths</button>
    <button class="button is-primary" @click="activeField='Active'">Active</button>
    <chart :labels="labels" :data="data"></chart>
</template>

<script>
import axios from 'axios';
import Chart from '../components/Chart.vue';
export default {
  components: { Chart },
    created(){
        axios.get('https://api.covid19api.com/dayone/country/' + this.$route.params.country).then(response => {
            console.log(response.data);
            this.dataset = response.data;
        });
    },
    data(){
        return {
            dataset: [],
            activeField: 'Confirmed'
        }
    },
    computed: {
        labels(){
            let nth = Math.floor(this.dataset.length/50);
            return this.dataset.map(data => data.Date).filter((data, key) => key%nth === 0);
        },
        data(){
            let nth = Math.floor(this.dataset.length/50);
            return this.dataset.map(data => data[this.activeField]).filter((data, key) => key%nth === 0);
        }
    }
}
</script>

<style>
</style>