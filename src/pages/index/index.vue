<template lang="pug">
  .container
    .faker-container
      faker(@fakerClick="onFakerClick")
        button.faker-button(formType="submit") 按钮
</template>

<script>
  import card from '@/components/card'
  import faker from '@/components/faker';

  export default {
    data() {
      return {
        motto: 'Hello World',
        userInfo: {}
      }
    },

    components: {
      card, faker
    },

    methods: {
      bindViewTap() {
        const url = '../logs/main'
        wx.navigateTo({url})
      },
      getUserInfo() {
        // 调用登录接口
        wx.login({
          success: () => {
            wx.getUserInfo({
              success: (res) => {
                this.userInfo = res.userInfo
              }
            })
          }
        })
      },
      clickHandle(msg, ev) {
        console.log('clickHandle:', msg, ev)
      }
    },

    created() {
      // 调用应用实例的方法获取全局数据
      this.getUserInfo()
    }
  }
</script>

<style lang="less" scoped>

  .faker-container {
    position: fixed;
    top: 140px;
    right: 0;

    .faker-button {
      font-size: 14px;
      font-weight: normal;
      padding: 0;
      width: 80px;
      justify-content: center;
      align-items: center;
      display: flex;
      height: 32px;
      background-color: #2979ff;
      border-radius: 15px 0 0 15px;
      font-family: FZLTHK--GBK1-0;
      color: #ffffff;
    }

    .faker-button::after {
      border: none;
    }

  }

</style>
