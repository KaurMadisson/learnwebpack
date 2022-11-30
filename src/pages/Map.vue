<template>
    <button class="button is-primary" @click="goToHome">Go To Home</button>
    <google-map :center="center" :zoom="zoom" :geoJson="coronaGeoJson" @centerChanged="updateCenter" @zoomChanged="updateZoom">
        <google-map-marker :pos="{ lat: 59.4269112, lng: 24.743487 }"></google-map-marker>
    </google-map>
</template>

<script>
import GoogleMap from '../components/GoogleMap.vue'
import GoogleMapMarker from '../components/GoogleMapMarker.vue';
import axios from 'axios';
export default {
  components: { GoogleMap, GoogleMapMarker },
  created(){
    axios.get('https://raw.githubusercontent.com/johan/world.geo.json/master/countries.geo.json')
    .then(response => {
        this.geoJson = response.data;
    });
    axios.get('https://api.covid19api.com/summary').then(response => {
            console.log(response.data);
            this.countries = response.data.Countries;
    });
  },
  data(){
    return {
        center: { lat: 59.4269112, lng: 24.743487 },
        zoom: 18,
        geoJson: null,
        countries: []
    }
  },
  methods:{
    goToHome(){
        this.center={lat:59.410645, lng: 24.605453};
        this.zoom=18;
    },
    updateCenter(newCenter){
        this.center = newCenter;
    },
    updateZoom(newZoom){
        this.zoom = newZoom;
    }
  },
  computed: {
    coronaGeoJson(){
        if(this.geoJson && this.countries){
            let geoJson = JSON.parse(JSON.stringify(this.geoJson));
            geoJson.features = geoJson.features.map(feature => {
                let country = this.countries.find(country => country.Country === feature.properties.name);
                if(country){
                    feature.properties.totalConfirmed = country.TotalConfirmed;
                } else {
                    feature.properties.totalConfirmed = -1;
                }
                return feature;
            });
            return geoJson;
        }
        
    }
  }
}
</script>

<style>
</style>