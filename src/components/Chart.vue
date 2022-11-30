<template>
  <canvas ref="myCanvas" width="600" height="300"></canvas> 
</template>

<script>
import Chart from 'chart.js/auto';
import { shallowRef } from 'vue';
export default {
    props: ['data', 'labels'],
    mounted(){
        let canvas = this.$refs['myCanvas'];
        console.log(canvas);
        this.chart = shallowRef(new Chart(canvas, {
            type: 'line',
            data: {
                labels: this.labels,
                datasets: [{
                    label: '# of Votes',
                    data: this.data,
                    borderColor: '#BADA55',
                }]
            }
        }));
        
    },
    data(){
        return {
            chart: null
        }
    },
    watch: {
        data(newData){
               this.chart.data.datasets[0].data = newData;
               this.chart.update();
        },
        labels(newLabels){
            this.chart.data.labels = newLabels;
            this.chart.update();
        }
    }
}
</script>

<style>
</style>