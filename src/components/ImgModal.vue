<template>
  <button class="modal-close is-large" aria-label="close" @click="$emit('close')"></button>
      <p class="image is 4by3">
      <img :src="src" alt="">
      </p>
      
      

</template>

<script>
export default {
    props: ['active','src']

}
</script>

<style>

</style>