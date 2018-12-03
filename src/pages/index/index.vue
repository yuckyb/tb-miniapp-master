<template>
  <div class="container">
    <van-search :value="searchValue" placeholder="请输入搜索关键词" />
    <swiper :indicator-dots="indicatorDots"
        :autoplay="autoplay" :interval="interval" :duration="duration">
        <block v-for="(item,index) in imgUrls" :key="index">
            <swiper-item>
            <img :src="item" class="slide-image" mode='widthFit' />
            </swiper-item>
        </block>
    </swiper>
  </div>
</template>

<script>
import card from '@/components/card'
export default {
  data () {
    return {
      searchValue:'',
    imgUrls: [    
    'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
    'https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1543839162572&di=72f9f4da6a0d21e24d74a8608b4aea0f&imgtype=0&src=http%3A%2F%2F5b0988e595225.cdn.sohucs.com%2Fimages%2F20180415%2F499dfbc8a48d40439bb2737693e23e93.jpeg',
    'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
    ],
    //是否显示指适点
    indicatorDots: true,
    //是否轮播
    autoplay: true,
    //
    interval: 5000,
    duration: 1000,
    inputShowed:false,
    inputVal:"",
    //轮播页当前index
    swiperCurrent:0, 
    }
  },

  components: {
    card
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    getUserInfo () {
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
    clickHandle (msg, ev) {
      console.log('clickHandle:', msg, ev)
    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    this.getUserInfo()
  }
}
</script>

<style scoped>
swiper-item{
  width: 100%;
  height: auto;
}
 img{
   width: 100%;
   height: 100%;
  }
.userinfo {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.userinfo-avatar {
  width: 128rpx;
  height: 128rpx;
  margin: 20rpx;
  border-radius: 50%;
}

.userinfo-nickname {
  color: #aaa;
}

.usermotto {
  margin-top: 150px;
}

.form-control {
  display: block;
  padding: 0 12px;
  margin-bottom: 5px;
  border: 1px solid #ccc;
}

.counter {
  display: inline-block;
  margin: 10px auto;
  padding: 5px 10px;
  color: blue;
  border: 1px solid blue;
}
</style>
