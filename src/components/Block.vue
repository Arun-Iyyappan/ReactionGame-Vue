<template>
    <div @click="stopTimer" class="block" v-if="show">Click Me  </div>
</template>

<script>
export default {
   props:['delay'],
   data(){
    return{
        show:false,
        timer :null,
        reactionTime : 0,
    }
   },
  mounted(){
     setTimeout(()=>{
           this.show= true;
           this.startTimer()
     }, this.delay)
  },
   methods:{
    startTimer(){
        this.timer = setInterval(()=>{
            this.reactionTime +=10
        },10)
    },
    stopTimer(){
        clearInterval(this.timer)
        this.$emit('end' , this.reactionTime)
    }
   }
}
</script>

<style>
.block{
    width: 400px;
    background-color: crimson;
    color:aqua;
    text-align: center;
    border-radius: 20px;
    margin : 50px auto;
    padding: 100px 0;
}
</style>