<script lang="ts">
import Block from './Block.vue'

export default {
  data() {
    return { isPlaying: false, delay: 0, score: 0 }
  },
  components: {
    Block
  },
  methods: {
    handleStart() {
      this.isPlaying = true
      this.score = 0
      this.delay = Math.random() * 1000
    },
    handleEnd(record: number) {
      this.score = record
      this.isPlaying = false
    }
  }
}
</script>

<template>
  <div class="main">
    <h3>REACTION TIME: {{ score > 0 ? score : ' - ' }} ms</h3>
    <button @click="handleStart" :disabled="isPlaying">
      {{ isPlaying ? 'GO...!' : 'START!' }}
    </button>
    <Block v-if="isPlaying" :delay="delay" @end="handleEnd" />
  </div>
</template>

<style>
body {
  background-color: #213363;
  font-family: 'Courier New', Courier, monospace;
}

.main {
  display: flex;
  justify-content: center;
  width: 100vw;
  height: 100vh;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  padding-top: 50px;
}
button {
  transition: all 0.5s ease;
  color: #fff;
  border: 3px solid white;
  text-transform: uppercase;
  text-align: center;
  font-size: 17px;
  background-color: transparent;
  padding: 10px 25px;
  outline: none;
  border-radius: 4px;
  cursor: pointer;
  margin-bottom: 20px;
}

button:disabled {
  cursor: unset;
}
button:hover {
  color: #001f3f;
  background-color: #fff;
}
button:disabled:hover {
  color: #001f3f;
  background-color: gray;
}

h3 {
  color: #d3d04f;
  mb: 3;
}
</style>
