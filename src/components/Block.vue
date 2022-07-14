<template>
  <div id="md-bg">
    <div class="block" v-if="showBlock" @click="this.stopTimer">
      {{ msg }}
    </div>
    <p class="rt">Reaction Time:{{ reactionTime }}ms</p>
  </div>
</template>

<script>
export default {
  name: "Block",
  data() {
    return {
      msg: "START PLAY",
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  props: ["delay"],
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
      console.log(this.reactionTime);
    },
  },
};
</script>

<style scoped>
.block {
  width: 400px;
  border-radius: 20px;
  background: #000000;
  color: rgb(255, 255, 255);
  padding: 100px 0;
  margin: 150px auto;
}
.rt {
  background-color: bisque;
  color: black;
  min-height: 70px;
  margin-left: 20%;
  padding: 15px;
  margin-top: 50px;
  border-radius: 20px;
  padding-top: 27px;
  margin-right: 20%;
}
#md-bg {
  bottom: 0;
  position: fixed;
  background: rgba(105, 51, 15, 0.658);
  width: 100%;
  height: 100%;
}
</style>
