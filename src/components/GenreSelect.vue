<template>
  <div >
   <select class="form-select" name="Genres" id="genreSelect"
    @change="$emit('genreSelected',genreInput)" v-model="genreInput"  >
        <option value="" selected>All</option>
        <option value="rock">Rock</option>
        <option value="pop">Pop</option>
        <option value="jazz">Jazz</option>
        <option value="metal">Metal</option>
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
}
</script>

<style>
#genreSelect{
    position: absolute;
    right: -5rem;
    width: 100px;
}
</style>