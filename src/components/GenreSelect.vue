<template>
  <div >
   <select class="form-select" name="Genres" id="genreSelect"
    @change="$emit('genreSelected', genreInput)" v-model="genreInput"  >
        <option value="" selected>All</option>
        <option v-for="(genre, index) in genres" :value="genre" :key="index" >
            {{genre}}
        </option>

    </select>
  </div>
</template>

<script>
export default {
    data() {
        return {
            genreInput:''
        }
    },
    props:{
        genres : Array
    }
}
</script>

<style>
#genreSelect{
    position: absolute;
    right: -5rem;
    width: 100px;
}
</style>