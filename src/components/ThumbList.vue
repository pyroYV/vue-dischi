<template>
    <div>
        <Loader class="loader" v-if="(!isLoaded)"/>
        <div class="row g-4 justify-content-center position-relative" v-if="(isLoaded)">
            <GenreSelect
            @genreSelected='GenreSelectedCallback'
            :genres = 'genres'/>
            <ArtistSelect
            @artistSearch = 'ArtistSelectCallback'
            @keyup.enter="FilterAlbumAuthor(artistSearch)"/>
            <SingleCard class="col-2" 
            v-for="(element, index) in filteredAlbums" :key="index"
                :card ="element"/>
        </div>
   </div>
</template>

<script>
import axios from 'axios'
import SingleCard from './SingleCard.vue'
import Loader from './Loader.vue'
import GenreSelect from './GenreSelect.vue'
import ArtistSelect from "./ArtistSelect.vue";

export default {
    data() {
        return {
            albumsArray:[],
            isLoaded:false,
            genres:[],
            genreSelected:'',
            filteredAlbums:[],
            artistSearch:'',
            artists: [],



        }
    },
    components:{
        SingleCard,
        Loader,
        GenreSelect,
        ArtistSelect,

    },
    methods: {
        GetCards(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((result) => {

                this.card = result.data.result;
                this.albumsArray = result.data.response

                this.GenreArray()
                this.FilterAlbumsGenre(this.genreSelected)

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
            }
            console.log(this.genres)
        },
        FilterAlbumsGenre(element){ 
            this.filteredAlbums = [...this.albumsArray].filter((album) => album.genre.includes(element))
        },
        GenreSelectedCallback(input){
            this.genreSelected = input
            this.FilterAlbumsGenre(this.genreSelected)
        },
        ArtistSelectCallback(input){
            this.genreSelected = input

        },
        FilterAlbumAuthor(element){
            this.filteredAlbums = [...this.albumsArray].filter((album) => album.author.toLowerCase().Iincludes(element.toLowerCase()))
        },
        ArtistsArray(){
            for(let i =0 ; i< this.albumsArray.length; i++){
            if(!this.artists.includes(this.albumsArray[i].author)){
                this.artists.push(this.albumsArray[i].author)
            }
            }
            console.log(this.artists)
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