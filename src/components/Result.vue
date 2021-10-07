<template>
  <h4>Reaction Time - {{score}}ms</h4>
  <h2 class="ranks">{{rank}}</h2>
</template>

<script>
export default {
props: ['score'],
data() {
    return {
        rank: null
    }
    
},
mounted() {
    if(this.score < 300){
        this.rank = "Lightning Fast"
    }else if(this.score <500){
        this.rank = "Very Fast"
    }else if(this.score <700){
        this.rank = "Slow"
    }else{
        this.rank = "Too Slow"
    }
},
}
</script>

<style>
.ranks{
    font-size: 1.4rem;
    color: #0faf87;
    font-weight: bold;
}

</style>