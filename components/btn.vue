<template>
  <div class="btn-area">
    <button
      v-for="item in msg"
      :key="item.category"
      class="btn"
      @click="select(item, level)"
    >
      {{ item.category }}
    </button>
    <button v-if="level !== 1 && level !== 4" class="btn" @click="back(level)">
      一つ前に戻る
    </button>
    <button v-if="level === 4" class="btn" @click="clear()">
      最初からやり直す
    </button>
  </div>
</template>

<script>
export default {
  props: ['msg', 'level'],

  methods: {
    select(item, level) {
      if (level === 1) {
        this.$parent.firstSelectList = item
      } else if (level === 2) {
        this.$parent.secondSelectList = item
      } else if (level === 3) {
        this.$parent.thirdSelectList = item
      }

      this.$emit('selected')
    },

    back(level) {
      if (level === 2) {
        this.$parent.firstSelectList = ''
        this.$parent.firstClick = false
      } else if (level === 3) {
        this.$parent.secondSelectList = ''
        this.$parent.secondClick = false
      }
    },

    clear() {
      this.$parent.firstClick = false
      this.$parent.secondClick = false
      this.$parent.thirdClick = false
      this.$parent.firstSelectList = ''
      this.$parent.secondSelectList = ''
      this.$parent.thirdSelectList = ''
    },
  },
}
</script>

<style lang="scss" scoped>
.btn-area {
  display: block;
  width: 90%;

  .btn {
    appearance: none;
    background: #fff;
    border: none;
    border-radius: 10px;
    cursor: pointer;
    font-size: 12px;
    margin: 0 10px 10px 0;
    outline: none;
    padding: 7px 10px;
    text-align: left;
    width: 100%;
  }
}
</style>
