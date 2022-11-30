<template>
    <div class="columns">
        <div class="column is-three-quarters">
            <input class="input" v-model="search">
        </div>
        <div class="column">
            <div class="select">
                <select v-model="sort">
                    <option v-for="option in sortOptions" :key="option.name" :value="option">{{option.name}}</option>
                </select>
            </div>
        </div>
    </div>
    
  <div class="columns is-multiline" v-if="countries">
    <div v-for="country in sortedCountries" :key="country.ID" class="column is-one-quarter">
        <country-card :country="country"></country-card>
    </div>
  </div>
  <h1 v-if="message">{{message}}</h1>
</template>

<script>
import axios from 'axios';
import CountryCard from '../components/CountryCard.vue';
export default {
  components: { CountryCard },
    created() {
        axios.get('https://api.covid19api.com/summary').then(response => {
            console.log(response.data);
            this.countries = response.data.Countries;
            this.message = response.data.Message;
        });
    },
    data() {
        return {
            countries: [],
            message: '',
            search: '',
            sortOptions: [
                {name: 'Name Asc', field: 'Country', order: 'asc'},
                {name: 'New Confirmed Asc', field: 'NewConfirmed', order: 'asc'},
                {name: 'New Deaths Asc', field: 'NewDeaths', order: 'asc'},
                // {name: 'New Recovered Asc', field: 'NewRecovered', order: 'asc'},
                {name: 'Total Confirmed Asc', field: 'TotalConfirmed', order: 'asc'},
                {name: 'Total Deaths Asc', field: 'TotalDeaths', order: 'asc'},
                // {name: 'Total Recovered Asc', field: 'TotalRecovered', order: 'asc'},
                {name: 'Name Desc', field: 'Country', order: 'desc'},
                {name: 'New Confirmed Desc', field: 'NewConfirmed', order: 'desc'},
                {name: 'New Deaths Desc', field: 'NewDeaths', order: 'desc'},
                // {name: 'New Recovered Desc', field: 'NewRecovered', order: 'desc'},
                {name: 'Total Confirmed Desc', field: 'TotalConfirmed', order: 'desc'},
                {name: 'Total Deaths Desc', field: 'TotalDeaths', order: 'desc'},
                // {name: 'Total Recovered Desc', field: 'TotalRecovered', order: 'desc'},
            ],
            sort: {name: 'Name Asc', field: 'Country', order: 'asc'}
        }
    },
    computed: {
        filteredCountries(){
            return this.countries.filter(country => {
                    return country.Country.substr(0, this.search.length).toLowerCase() == this.search.toLowerCase()
            });
        },
        sortedCountries(){
            return this.filteredCountries.sort((a, b) => {
                let order = this.sort.order == 'asc' ? 1 : -1;
                if(a[this.sort.field] < b[this.sort.field]){
                    return -1 * order;
                } else if(a[this.sort.field] > b[this.sort.field]) {
                    return 1 * order;
                }
                return 0;
            });
        }
    }
}
</script>

<style>
</style>