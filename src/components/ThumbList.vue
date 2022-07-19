<template>
  <div>
    <SingleCard/>
  </div>
</template>

<script>
import axios from 'axios'
import SingleCard from './SingleCard.vue'

export default {
    data() {
        return {
            
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
                console.log(result.data.result)
            })
            .catch((error) => {
                console.warn(error);
            })
        }
    },

}
</script>

<style>

</style>