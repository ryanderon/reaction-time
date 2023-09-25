<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h4>Click Me</h4>
  </div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay);
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10);
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 16px;
  background: #0faf87;
  color: white;
  cursor: pointer;
  text-align: center;
  padding: 50px 0;
  margin: 40px auto;
}
</style>
