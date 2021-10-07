<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Click Me
  </div>
</template>

<script>
export default {
    props: ['delay'],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0
        }
    },
    mounted() {
        console.log("Component Mounted")
        setTimeout(() => {
            this.showBlock = true
            this.startTimer()
            console.log(this.delay)
        }, this.delay);
    },
    methods: {
        startTimer(){
            this.timer = setInterval(()=>{
                this.reactionTime += 10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            console.log(this.reactionTime)
        }
    },
    // updated() {
    //     console.log("component Updated")
    // },
    // unmounted() {
    //     console.log("component Unmounted")
    // },

}
</script>

<style>
.block{
    width: 400px;
    border-radius: 16px;
    background: #0faf87;
    color: aliceblue;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
}

</style>