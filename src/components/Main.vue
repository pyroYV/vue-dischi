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
main{
    background-color: #1e2d3b;
    height: 80vh;
}

</style>