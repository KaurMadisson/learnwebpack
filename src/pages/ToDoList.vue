<template>
  <div class="container">
    <section class="section">
      <div class="field has-addons">
        <p class="control">
        <input class="input" type="text" v-model="newItem" @keydown.enter = "addItem()">
        </p>
        <p class="control">
      <button class="button" @click="addItem()">Add</button>
        </p>
      </div>

      
      <div class="content">
        <item-list title="All Items" :items="items"></item-list>
        <item-list title="Done Items" :items="DoneItems"></item-list>
        <item-list title="Not Done Items" :items="notDoneItems"></item-list>
      </div>
    </section>
    </div>
  </template>
  
  <script>
import ItemList from '../components/ItemList.vue';
  export default {
  components: { ItemList },
      data(){
          return{
              newItem: '',
              count: 0,
              items: [
                {name:'sai', done: true, id: 0},
                {name:'viin', done: false, id: 1},
                {name:'piim', done: false, id: 2},
              ]
          }
      },
      methods: {
        addItem(){
          if(this.newItem !=""){
          this.items.push({name:this.newItem, done: false, id: this.items.length});
          }
          this.newItem = '';
        }
      },
      computed: {
        DoneItems(){
          return this.items.filter(item => item.done);
        },
        notDoneItems(){
          return this.items.filter(item => !item.done);
      }
    }
  }
  </script>
  
  <style>
  
  </style>