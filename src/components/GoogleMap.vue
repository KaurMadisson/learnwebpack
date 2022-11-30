<template>
  <div ref="map" id="map"></div>
  <slot></slot>
</template>

<script>
import { Loader } from "@googlemaps/js-api-loader";
import { shallowRef } from 'vue';
export default {
    mounted(){
        const loader = new Loader({
            apiKey: "AIzaSyCFZquZ6fD9XiCi_1Pv9KVBhu5Qj8ukpy4",
            version: "weekly"
        });
        loader.load().then(() => {
            this.map = shallowRef(new google.maps.Map(this.$refs['map'], {
                center: this.center,
                zoom: this.zoom,
                // styles: [
                //     {
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "color": "#1d2c4d"
                //         }
                //         ]
                //     },
                //     {
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#8ec3b9"
                //         }
                //         ]
                //     },
                //     {
                //         "elementType": "labels.text.stroke",
                //         "stylers": [
                //         {
                //             "color": "#1a3646"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "administrative",
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "visibility": "off"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "administrative.country",
                //         "elementType": "geometry.stroke",
                //         "stylers": [
                //         {
                //             "color": "#4b6878"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "administrative.land_parcel",
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#64779e"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "administrative.province",
                //         "elementType": "geometry.stroke",
                //         "stylers": [
                //         {
                //             "color": "#4b6878"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "landscape.man_made",
                //         "elementType": "geometry.stroke",
                //         "stylers": [
                //         {
                //             "color": "#334e87"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "landscape.natural",
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "color": "#023e58"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "poi",
                //         "stylers": [
                //         {
                //             "visibility": "off"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "poi",
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "color": "#283d6a"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "poi",
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#6f9ba5"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "poi",
                //         "elementType": "labels.text.stroke",
                //         "stylers": [
                //         {
                //             "color": "#1d2c4d"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "poi.park",
                //         "elementType": "geometry.fill",
                //         "stylers": [
                //         {
                //             "color": "#023e58"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "poi.park",
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#3C7680"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road",
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "color": "#304a7d"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road",
                //         "elementType": "labels.icon",
                //         "stylers": [
                //         {
                //             "visibility": "off"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road",
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#98a5be"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road",
                //         "elementType": "labels.text.stroke",
                //         "stylers": [
                //         {
                //             "color": "#1d2c4d"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road.highway",
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "color": "#2c6675"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road.highway",
                //         "elementType": "geometry.stroke",
                //         "stylers": [
                //         {
                //             "color": "#255763"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road.highway",
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#b0d5ce"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "road.highway",
                //         "elementType": "labels.text.stroke",
                //         "stylers": [
                //         {
                //             "color": "#023e58"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "transit",
                //         "stylers": [
                //         {
                //             "visibility": "off"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "transit",
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#98a5be"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "transit",
                //         "elementType": "labels.text.stroke",
                //         "stylers": [
                //         {
                //             "color": "#1d2c4d"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "transit.line",
                //         "elementType": "geometry.fill",
                //         "stylers": [
                //         {
                //             "color": "#283d6a"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "transit.station",
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "color": "#3a4762"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "water",
                //         "elementType": "geometry",
                //         "stylers": [
                //         {
                //             "color": "#0e1626"
                //         }
                //         ]
                //     },
                //     {
                //         "featureType": "water",
                //         "elementType": "labels.text.fill",
                //         "stylers": [
                //         {
                //             "color": "#4e6d70"
                //         }
                //         ]
                //     }
                //     ]
            }));
            this.map.addListener("center_changed", () => {
                clearTimeout(this.centerTimeout);
                this.centerTimeout = setTimeout(()=> {
                    this.$emit('centerChanged', {
                        lat: this.map.getCenter().lat(),
                        lng: this.map.getCenter().lng()
                    });
                }, 1000);
                
            });
            this.map.addListener("zoom_changed", () => {
                this.$emit('zoomChanged', this.map.getZoom());
            });
            console.log(this.map.data);
            this.map.data.addGeoJson(this.geoJson);
            this.map.data.setStyle(function(feature) {
                let confirmed = feature.getProperty('totalConfirmed');
                                  
                var color = confirmed > 10_000_000 ? 'red' : 
                            confirmed > 1_000_000 ? '#F74725' :
                            confirmed > 100_000 ? '#F59204' :
                            confirmed > 10_000 ? '#F5C807' :
                            confirmed > 1000 ? '#E9F502' :
                            confirmed > 100 ? '#87F501' :
                            confirmed >= 0 ? 'green' : 'black';
                return {
                    fillColor: color,
                    strokeWeight: 1
                };
            });
        });
    },
    props: ['center', 'zoom', 'geoJson'],
    data(){
        return {
            map: null,
            centerTimeout: null
        }
    },
    watch: {
        center(newCenter){
            console.log(this.map);
            this.map.panTo(newCenter);
        },
        zoom(newZoom){
            console.log(newZoom);
            this.map.setZoom(newZoom);
        },
        geoJson(newGeoJson){
            if(this.map){
                this.map.data.addGeoJson(newGeoJson);
                this.map.data.setStyle(function(feature) {
                    let confirmed = feature.getProperty('totalConfirmed');
                    if(feature.getProperty('name') == 'Russia'){
                        console.log(confirmed);
                    }
                    var color = confirmed > 10_000_000 ? 'red' : 
                                confirmed > 1_000_000 ? '#F74725' :
                                confirmed > 100_000 ? '#F59204' :
                                confirmed > 10_000 ? '#F5C807' :
                                confirmed > 1000 ? '#E9F502' :
                                confirmed > 100 ? '#87F501' :
                                confirmed >= 0 ? 'green' : 'black';
                    return {
                        fillColor: color,
                        strokeWeight: 1
                    };
                });
            }
        }
    }
}
</script>

<style scoped>
#map {
  height: 80vh;
}
</style>