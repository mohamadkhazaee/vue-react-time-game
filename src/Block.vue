<template>
  <div @click="endTimer" v-if="showBlock">CLICK ME!</div>
</template>

<script lang="ts">
export default {
  props: ['delay'],
  data() {
    return { showBlock: false, timer: 0, reactionTime: 0 }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true
      this.startTimer()
    }, this.delay)
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    endTimer() {
      this.$emit('end', this.reactionTime)
      this.showBlock = false
      clearInterval(this.timer)
    }
  },
  updated() {}
}
</script>

<style scoped>
div {
  background-color: #17594a;
  width: 400px;
  height: 400px;
  display: block;
  color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 30px;
  border-radius: 30px;
}
</style>
