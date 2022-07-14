<template>
  <div class="scoree">
    <p class="res">score:{{ score }}ms</p>
    <legend class="legend">{{ rank }}</legend>
  </div>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "You are really quick Master";
    } else if (this.score < 450) {
      this.rank = "You Almost caught Master you Are A Deer";
    } else {
      this.rank = "You are a snail or A tortoise TRY mastery";
    }
  },
};
</script>

<style scoped>
.scoree {
  background-color: bisque;
  min-height: 80px;
  text-align: center;
  border-radius: 10px;
  padding: 10px;
  padding-bottom: 50px;
  margin-left: 20%;
  margin-right: 20%;
  padding-top: 45px;
  font-size: 23px;
}
.res {
  border-bottom: 1px solid red;
  margin-left: 40%;
  margin-right: 40%;
}
.legend {
  border-bottom: 1px solid red;
  margin-left: 17%;
  margin-right: 17%;
}
</style>