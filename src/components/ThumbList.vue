<template>
  <div class="row g-4 justify-content-center">
    <SingleCard class="col-2"
     v-for="(element, index) in albumsArray" :key="index"
        :card ="element"
     />
  </div>
</template>

<script>
import axios from 'axios'
import SingleCard from './SingleCard.vue'


export default {
    data() {
        return {
            albumsArray:[],
 
        }
    },
    components:{
        SingleCard,
    },
    methods: {
        GetCards(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {
                this.card = result.data.result;
                this.albumsArray = result.data.response
                console.log(this.albumsArray)
            })
            .catch((error) => {
                console.warn(error);
            })
        }
    },
    mounted() {
        this.GetCards()
    },

}
</script>

<style>

</style>