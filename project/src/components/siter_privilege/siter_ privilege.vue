<template>
<div class="siter_big_wrap">
    <div v-wechat-title="$route.meta.title"></div>
        <!-- 个人信息 -->
    <div class="siter_wrap">
        <div class="siter_per_left">
            <img :src="siteInfoText.user_thumbnail" alt="">
            <div class="siter_name_wrap">
                <p>{{ siteInfoText.user_nickname}}</p>
                <img src="../../../static/siter_privilege/img/queen.png" alt="">
                <span>{{ siteInfoText.owner_phone }}</span>
                <p class="jue_se">点位主</p>
            </div>
        </div>
        <div class="siter_people">
            <span>{{ customerNum }}</span>
            <span>/顾客</span>
        </div>
    </div>

    <!-- 选择列表 -->
    <ul class="siter_ul">
        <li  @click="toNextPage(0)">
            <img src="../../../static/siter_privilege/img/my_buser.png" alt="">
            <p>我的顾客</p>
            <img src="../../../static/siter_privilege/img/left.png" alt="">
        </li>
        <li @click="toNextPage(1)">
            <img src="../../../static/siter_privilege/img/my_active.png" alt="">
            <p>我发布的活动</p>
            <img src="../../../static/siter_privilege/img/left.png" alt="">
        </li>
    </ul>

    <!-- 活动展示 -->
    <ul class="siter_active" style="height: 4rem;overflow: hidden;">
        <li v-for="(item,index) in advList" @click="advDetails()">
            <img src="../../../static/siter_privilege/img/317630780744939915.png" alt="">
        </li>
        <li>
            <img src="../../../static/siter_privilege/img/317630780744939915.png" alt="">
        </li>
        <li>
            <img src="../../../static/siter_privilege/img/317630780744939915.png" alt="">
        </li>
    </ul>
    <!-- 查看更多 -->
    <div class="check_more" @click="goMore()">
        查看更多
    </div>

</div>
</template>

<script>
export default {
  data () {
    return {
      siteInfoText: '',
      customerNum: 0,
      advList: ''
    }
  },
  methods: {
    toNextPage: function (index) {
      if (index === 0) { // 我的顾客
        this.$router.push({
          path: '/myCustomer'
        })
      } else { // 我的活动
        this.$router.push({
          path: '/myActivity'
        })
      }
    },
    // 获取点位主信息
    getSiterInfo: function () {
      this.$axios.get('api/wxpub/siter/getSiterInfo.html')
        .then((res) => {
          if (res.data.code === 200) {
            this.siteInfoText = res.data.data.siterInfo // 点位主信息
            this.advList = res.data.data.siterPromotion // 发布的活动列表
          }
        })
        .catch((err) => {
          console.log(err)
        })
    },
    // 获取顾客总数
    customerList: function () {
      this.$axios.get('api/wxpub/siter/getUserList.html')
        .then((res) => {
          if (res.data.code === 200) {
            this.customerNum = res.data.data.total
            // Indicator.close()
          }
        })
        .catch((err) => {
          console.log(err)
        })
    },
    // 跳转更多
    goMore: function () {
      this.$router.push({
        path: '/myActivity'
      })
    },
    // 单个活动点击
    advDetails: function () {
      this.$router.push({
        path: '/actDetail',
        query: {
          code: '1'
        }
      })
    }

  },
  beforeCreate: function () {

  },
  created: function () {
    // this.imgUrl =
    // this.getuserInfo()
    this.getSiterInfo()
    this.customerList()
  },
  beforeMount: function () {

  },
  mounted: function () {
    // this.timeDown()
    // this.getSiterInfo()
  }

}
</script>

<style scoped>
@import '../../../static/siter_privilege/css/siter_privilege.css';
.siter_big_wrap{
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: #F3F6F5;
}
</style>
