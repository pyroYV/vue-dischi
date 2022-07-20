<template>
<main>
    <div class="container-lg"> 
        
     <ThumbList/>
  </div>
</main>
</template>

<script>
import ThumbList from './ThumbList.vue'
export default {
    components:{
        ThumbList,
    }
}
</script>

<style lang="scss" scoped>
@import '../assets/styles/variables.scss';
main{
    background-color: $BrandBlue;
    height: 90vh;
}

</style>