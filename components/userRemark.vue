<template>
  <div class="remark-area">
    <p class="remark">{{ msg }}</p>
  </div>
</template>

<script>
export default {
  props: ['msg'],
}
</script>

<style lang="scss" scoped>
.remark-area {
  display: block;
  float: right;
  height: auto;
  margin: 1.5em 0;
  text-align: right;
  width: 90%;

  .remark {
    background: #f1d8e7;
    border-radius: 10px;
    color: #333;
    display: inline-block;
    max-width: 100%;
    min-height: 1.5em;
    min-width: 10px;
    padding: 7px 10px;
  }
}
</style>
