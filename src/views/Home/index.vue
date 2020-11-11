<template>
  <div class="page-home">
    <section class="go-top font-20">
      <div class="icon-arrow-up"></div>
    </section>

    <header class="index-header">
      <a href="mine.html?cpid=0">
        <div class="header-user">
          <div class="user-btn"></div>
        </div>
      </a>
      <div class="header-logo"></div>
      <a href="search.html?cpid=0">
        <div class="header-search"></div>
      </a>
    </header>
    <Swiper :autoplay = "2000" >
      <SwipeItem>1</SwipeItem>
      <SwipeItem>2</SwipeItem>
      <SwipeItem>3</SwipeItem>
      <SwipeItem>4</SwipeItem>
    </Swiper>
    <Swiper :autoplay = "2000" >
      <SwipeItem>1</SwipeItem>
      <SwipeItem>2</SwipeItem>
      <SwipeItem>3</SwipeItem>
      <SwipeItem>4</SwipeItem>
    </Swiper>
  </div>
</template>

<script>
import { Swiper, SwipeItem } from '@/components/Swiper'
import { getBanner } from '@/api/cartoon'
export default {
  name: 'Home',
  components: {
    Swiper,
    SwipeItem
  },
  created () {
    getBanner().then(res => { console.log(res) })
  }
}
</script>

<style lang="scss" scoped>
@import "~@/assets/style/mixins.scss";
// .page-home{
//   display: flex;
//   height: 100%;
//   flex-direction: column;
// }
  .index-header{
    @include border-bottom;
    position: relative;
    display: flex;
    height: 44px;
    justify-content: space-between;
    align-items: center;
    padding: 0 20px;
    box-sizing: border-box;
    // &::after{
    //   content: '';
    //   position: absolute;
    //   width: 100%;
    //   height: 1px;
    //   bottom: 0;
    //   left: 0;
    //   border-bottom: 1px solid #ededed;
    //   transform: scaleY(.5);
    // }
  }
  .user-btn{
    width: 25px;
    height: 25px;
    background: url(~@/assets/icon/user-btn.png);
    background-size: 100%;
  }
  .header-logo{
    width: 92px;
    height: 28px;
    background: url(~@/assets/logo.png) no-repeat;
    background-size: 100%;
  }
  .header-search{
    width: 25px;
    height: 25px;
    background: url(~@/assets/icon/search.png) no-repeat;
    background-size: 100%;
  }
</style>
