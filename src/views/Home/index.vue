<template>
  <div class="page-home">
    <section class="go-top font-20">
      <div class="icon-arrow-up"></div>
    </section>

    <index-header></index-header>
    <indexNav></indexNav>
    <div class = "index-main">
      <Swiper :autoplay = "2000" class="myswiper" v-if = "bannerList.length > 0">
        <SwipeItem v-for = "item in bannerList" :key = "item.id" >
          <img
            :src="item.imageurl"
          />
        </SwipeItem>
      </Swiper>
      <index-recommend v-for = "item in recommentList" :key = 'item.specialid' :info = 'item'></index-recommend>
      <div class="my-icp">
        <a
          class="record"
          href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=31011202006214"
          target="_blank"
        >
          <img class="img" src="https://wechatapp.zhuishushenqi.com/mhd/201711/gongan.jpg" />
          <div>沪公网安备 31011202006214号</div>
        </a>
        <div class="licence">
          增值电信业务经营许可证沪B2-20170022
          <br />网络文化经营许可证沪网文（2016）3206-227号
          <br />出版物经营许可证新出发沪批字第U7659号
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Swiper, SwipeItem } from '@/components/Swiper'
import { getBanner, getIndexRecomment } from '@/api/cartoon'
import indexHeader from './components/indexHeader.vue'
import indexNav from './components/indexNav.vue'
import indexRecommend from './components/indexRecommend.vue'
export default {
  name: 'Home',
  data () {
    return {
      bannerList: [],
      recommentList: []
    }
  },
  components: {
    Swiper,
    SwipeItem,
    indexHeader,
    indexNav,
    indexRecommend
  },
  methods: {
    getBanner () {
      getBanner().then(res => {
        if (res.code === 200) {
          this.bannerList = res.info
        } else {
          alert(res.code_msg)
        }
      }).catch((err) => {
        alert('网络异常', err)
      })
    },
    getIndexRecomment () {
      getIndexRecomment().then(res => {
        if (res.code === 200) {
          this.recommentList = res.info
        } else {
          alert(res.code_msg)
        }
      }).catch((err) => {
        alert('网络异常', err)
      })
    }
  },
  created () {
    this.getBanner()
    this.getIndexRecomment()
  }
}
</script>

<style lang="scss" scoped>
.page-home{
  .index-main{
    flex: 1;
    overflow-y: auto;
  }
  display: flex;
  height: 100%;
  flex-direction: column;
}

  .myswiper img{
    width: 100%;
  }

  .my-icp {
  padding: 5px 0;
  font-size: 12px;
  .record {
    display: flex;
    align-items: center;
    justify-content: center;
    .img {
      width: 15px;
      height: 15px;
      margin-right: 4px;
    }
  }
  .licence {
    margin-top: 4px;
    text-align: center;
  }
}
</style>
