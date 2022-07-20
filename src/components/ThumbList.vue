<template>
    <div>
        <Loader class="loader" v-if="(!isLoaded)"/>
        <div class="row g-4 justify-content-center position-relative" v-if="(isLoaded)">
            <GenreSelect
            @genreSelected='genreSelected'
            />
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
import GenreSelect from './GenreSelect.vue'

export default {
    data() {
        return {
            albumsArray:[],
            isLoaded:false,
            genres:[],
            genreSelected:''

        }
    },
    components:{
        SingleCard,
        Loader,
        GenreSelect
    },
    methods: {
        GetCards(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {

                this.card = result.data.result;
                this.albumsArray = result.data.response

                this.GenreArray()

                this.Loading()
            })
            .catch((error) => {
                console.warn(error);
            })
        },
        Loading(){
            setTimeout(() => this.isLoaded = true ,/* 3000 */)
        },
        GenreArray(){
            
            for(let i =0 ; i< this.albumsArray.length; i++){
            if(!this.genres.includes(this.albumsArray[i].genre)){
                this.genres.push(this.albumsArray[i].genre)
            }
            console.log(this.genres)
        }
        }

    },
    mounted() {
        this.GetCards() 
        
    },

}
</script>

<style lang="scss">
loader{
    img{
        margin: auto;
    }
}
</style>