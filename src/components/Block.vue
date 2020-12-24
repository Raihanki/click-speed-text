<template>
  <div class="counter">{{ counter }}</div>
  <div class="block" @click.once="startCount" @click="counter++">
    Click Here
  </div>
  <div class="timer">
    <p class="timeout">Time : {{ timer }}</p>
  </div>
</template>

<script>
export default {
  props: ['isPlaying'],
  data() {
    return {
      counter: 0,
      timer: 5,
      start: false,
    }
  },
  methods: {
    startCount() {
      this.start = true;
      this.startTimer();
    },
    startTimer() {
      let interval = setInterval(() => {
        this.timer--;
        if ( this.timer === 0 ) {
          this.start = false;
          this.$emit('end', this.counter);
          clearInterval(interval);
        }
      }, 1000)
    }
  }
}
</script>

<style scoped>
  .block {
    width: 400px;
    border-radius: 20px;
    background: #0faf07;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
    font-size: large;
  }
  .counter {
    margin-bottom: -10px;
    margin-top: 20px;
    font-size: x-large;
  }
  .block {
    cursor: pointer;
  }
  .block[disabled] {
    cursor: not-allowed;
  }
  .timeout {
    margin-top: -10px;
    font-size: x-large;
  }
</style>