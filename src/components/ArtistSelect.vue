<template>
  <div id="">
    <input type="text" v-model='artistSearch' @change="$emit('artistSearch', artistSearch)" placeholder="Vuoi cercare per un artista?"> 
  </div>
</template>

<script>
export default {
    data() {
      return {
        artistSearch: ''
      }
    },
}
</script>

<style>
#ArtistSearch{
    position: absolute;
    right: -5rem;
    width: 100px;
}
</style>