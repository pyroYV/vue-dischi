<template>
  <div >
   <select class="form-select" name="Genres" id="genreSelect">
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

}
</script>

<style>
#genreSelect{
    position: absolute;
    right: -5rem;
    width: 100px;
}
</style>