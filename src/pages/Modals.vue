<template>

        <img-modal :active="active3" @close="active3=false" src="https://placebear.com/g/1280/960%22%3E"></img-modal>
        
        <modal :active="active" @close="active=false" src="https://placebear.com/g/1280/960%22%3E"></modal>
        <button class="button is-primary" @click="active=true">Open Modal</button>

         <modal :active="active2" @close="active2=false" src="https://placebear.com/g/1280/960%22%3E"></modal>
        <button class="button is-primary" @click="active2=true">Open Modal2</button>

        <modal :active="active3" @close="active3=false" src="https://placebear.com/g/1280/960%22%3E"></modal>
        <button class="button is-primary" @click="active3=true">Open Modal3</button>



</template>


<script>
import ImgModal from '../components/ImgModal.vue';
import Modal from '../components/Modal.vue';






    export default {
        components: {Modal},
            data(){
                return {
                    active: false,
                    active2: false,
                    active3: false,
                };
            },
            
    }


ImgModal



</script>

<style>

</style> 