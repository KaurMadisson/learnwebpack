<template>
  <h1>{{title}}</h1>
    <ul>
      <li v-for=" item in items " :key="item.id">
        {{ item.name }}
        <input type="checkbox" v-model ="item.done">
      </li>
    </ul>
</template>

<script>
export default {
    props: ['items', 'title']
}
</script>

<style>

</style>