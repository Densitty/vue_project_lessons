<template>
  <div v-if="showBlock" class="block" @click="stopTimer">
    click me
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
    };
  },
  mounted() {
    setTimeout(() => {
      console.log(this.delay);
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },
  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        // increase the reactionTime by 10ms
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      // when clearInterval is invoked, reactionTimer will not increase
      clearInterval(this.timer);
      console.log(this.reactionTime);
      this.$emit('end', this.reactionTime);
    }
  }
  // update() {
  //   console.log("component updated")
  // },
  // unmounted() {
  //   console.log("component unmounted")
  // }
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: #fff;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
