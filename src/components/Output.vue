<template>
    <p>Reaction Time : {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
</template>

<script>
import Block from './Block.vue';

export default {
   props:['score'],
   data(){
    return{
        rank:null
    }
   },
   mounted(){
     if( this.score < 250){
        this.rank = 'Reflex Master'
     } else if( this.score < 400){
        this.rank = 'Not Bad ...'
     }
     else{
        this.rank = 'Expected More....'
     }
   }
}
</script>

<style>
.rank{
    font-size: 1.4em;
    color:  aqua;
    font-weight: bold;
}
</style>