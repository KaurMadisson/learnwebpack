<template>
  <div class="tabs">
    <ul>
    
    <li @click="active=index" :class="{'is-active':active===index}" v-for="(link,index) in links" :key="index">
        <router-link :to= "link.path">{{link.name}}</router-link>
    </li>
  </ul>
  </div>
</template>

<script>
export default {
    props: ['links'],
    data(){
        return {
            active: 0,

        }
    }
}
</script>

<style>

</style>
