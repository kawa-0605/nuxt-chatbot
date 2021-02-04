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
  height: auto;
  margin: 1.5em 0;
  width: 90%;

  .remark {
    background: #d8e7f1;
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
