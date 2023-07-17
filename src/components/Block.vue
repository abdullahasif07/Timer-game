<template>
<div class="block" v-if="blockshow"  @click="stop_timer">
    Click me
</div>  
</template>

<script>
export default {
    props:['delay'],
    data() {
        return {
            blockshow:false,  
            timer:null,
            reaction_time:0 
        }
    },
    mounted()
    {
    console.log('mounted');
    setTimeout(() => {
      this.blockshow = true
      this.start_timer()
    }, this.delay);
    
  },
      
    methods: {
        start_timer()
        {
            this.timer=setInterval(() => {
                this.reaction_time+=10
            }, 10);
        },
        stop_timer()
        {
            clearInterval(this.timer);
            console.log(this.reaction_time);
            this.blockshow=false;
            this.$emit('endgame',this.reaction_time)
        }
    }, 
   
}
</script>

<style>
.block {
    
    width: 20%;
    height: 100px;
    background-color: green;
    color: white;
    position: fixed;
    top: 50%;
    left: 40%;
    
  }
  
</style>