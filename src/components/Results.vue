<template>
  <p>You clicked after {{ result }}ms.</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
  props: ['result'],
  data() {
    return {
      rank: null
    };
  },
  mounted() {
    if (this.result < 250) {
      this.rank = 'Switly Fingers!!!';
    } else if (this.result < 400) {
      this.rank = 'Fast Fingers ...';
    } else {
      this.rank = "Hire me as your reflex coach :')";
    }
  }
};
</script>

<style scoped>
.rank {
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>
