<template>
  <div class="single-card mx-3 p-2 text-center">
    <img :src="card.poster" alt="">
    <p>
        {{card.title}}
    </p>
    <p> {{card.author}} </p>
    <p>{{card.genre}}</p>
  </div>
</template>

<script> 
export default {
    props:[
        'card'
        ]

}
</script>

<style lang="scss">
    
.single-card{
    color:white;
    background-color: #2e3a46;
    img{
        height: 200px;
        width: 200px;
    }
}
</style>