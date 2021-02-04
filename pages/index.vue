<template>
  <div class="chatbot-window">
    <div class="header"></div>
    <div id="main">
      <div class="first">
        <ChatbotRemark
          :msg="'初めまして。何かお困りでしょうか？以下からお選びください。'"
        />
        <Btn
          v-if="!firstClick"
          :msg="msgData"
          :level="1"
          @selected="firstClick = true"
        />
      </div>
      <div v-if="firstClick" class="second">
        <UserRemark :msg="firstSelectList.category" />
        <ChatbotRemark
          :msg="`${firstSelectList.category}ですね。以下の選択肢からお選びください。`"
        />
        <Btn
          v-if="!secondClick"
          :msg="firstSelectList.data"
          :level="2"
          @selected="secondClick = true"
        />
      </div>
      <div v-if="secondClick" class="third">
        <UserRemark :msg="secondSelectList.category" />
        <ChatbotRemark
          :msg="`${secondSelectList.category}ですね。以下の選択肢からお選びください。`"
        />
        <Btn
          v-if="!thirdClick"
          :msg="secondSelectList.data"
          :level="3"
          @selected="thirdClick = true"
        />
      </div>
      <div v-if="thirdClick" class="fourth">
        <UserRemark :msg="thirdSelectList.category" />
        <ChatbotRemark
          :msg="`${thirdSelectList.category}ですね。回答は以下になります。`"
        />
        <ChatbotRemark :msg="thirdSelectList.answer" />
        <Btn :level="4" />
      </div>
    </div>
  </div>
</template>

<script>
// eslint-disable-next-line no-unused-vars
import ChatbotRemark from '~/components/chatbotRemark'
// eslint-disable-next-line no-unused-vars
import Btn from '~/components/btn'
// eslint-disable-next-line no-unused-vars
import UserRemark from '~/components/userRemark'
import data from '~/assets/data/data.js'

export default {
  data() {
    return {
      firstClick: false,
      secondClick: false,
      thirdClick: false,
      firstSelectList: [],
      secondSelectList: [],
      thirdSelectList: [],
    }
  },

  computed: {
    msgData: () => data,
  },

  updated() {
    this.scrollToEnd()
  },

  methods: {
    scrollToEnd() {
      const renderer = document.getElementById('main')
      renderer.scrollTop = renderer.scrollHeight
    },
  },
}
</script>

<style lang="scss" scoped>
.chatbot-window {
  border: 1px solid #262626;
  border-radius: 10px;
  font-size: 12px;
  height: 500px;
  margin: 10px;
  width: 300px;

  .header {
    background: #262626;
    border-bottom: 1px solid #262626;
    border-radius: 8px 8px 0 0;
    height: 5%;
    width: 100%;
  }

  #main {
    background: #eceff1;
    border-radius: 0 0 10px 10px;
    height: 95%;
    overflow-y: auto;
    padding: 10px;
  }
}
</style>
