<template>
  <div class="block" v-if="showBlock" @click="stopTimer">Click me</div>
</template>

<script>
export default {
  props: ["delay"],

  data() {
    return {
      showBlock: false,
      reactionTime: 0,
      timer: null,
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

<style scopes>
.block {
  width: 400px;
  margin: 50px auto;
  padding: 100px 0;
  color: white;
  border-radius: 20px;
  background: #0faf87;
}
</style>
