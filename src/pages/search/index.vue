<template>
  <div class="container">
    <van-search :value="searchValue" placeholder="请输入搜索关键词" />
    <van-badge-group :active="active" bind:change="onChange">
      <van-badge title="产品1" />
      <van-badge title="产品2" info="8" />
      <van-badge title="产品3" info="99" />
      <van-badge title="产品4" info="199" />
    </van-badge-group>
    <div>
      请输入搜索关键词请输入搜索关键词请输入搜索关键词请输入搜索关键词请输入搜索关键词请输入搜索关键词
    </div>
  </div>
</template>

<script>
import card from '@/components/card'
export default {
  data () {
    return {
      searchValue:'',
        active: 0
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
    onChange(event) {
      wx.showToast({
        icon: 'none',
        title: `切换至第${event.detail}项`
      });
    }
  },

  created () {
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
