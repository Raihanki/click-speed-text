<template>
  <div class="result">
    <span class="end">Game Over</span>
    <br>
    <span class="total">Total Click In 5 Seconds: <span class="resultClick">{{ resultClick }}</span></span>
  </div>
</template>

<script>
export default {
  props: ['resultClick'],
}
</script>

<style>
  .result {
    margin-top: 25px;
  }
  .end {
    color: #c42727;
    font-size: xx-large;
  }
  .total {
    font-size: x-large;
  }
  .resultClick {
    font-size: xxx-large;
    font-weight: bolder;
  }
</style>