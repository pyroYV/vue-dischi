<template>
    <div>
        <Loader v-if="(!isLoaded)"/>
    <div class="row g-4 justify-content-center" v-if="(isLoaded)">
        <SingleCard class="col-2" 
        v-for="(element, index) in albumsArray" :key="index"
            :card ="element"
        />
        
    </div>
   </div>
</template>

<script>
import axios from 'axios'
import SingleCard from './SingleCard.vue'
import Loader from './Loader.vue'

export default {
    data() {
        return {
            albumsArray:[],
            isLoaded:false
 
        }
    },
    components:{
        SingleCard,
        Loader,
    },
    methods: {
        GetCards(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {
                this.card = result.data.result;
                this.albumsArray = result.data.response
            })
            .catch((error) => {
                console.warn(error);
            })
        },
        Loading(){
            setTimeout(() => this.isLoaded = true ,3000)
          
        }
    },
    mounted() {
        this.Loading()
        this.GetCards()
       
        
    },

}
</script>

<style>

</style>