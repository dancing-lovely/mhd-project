<template>
  <div class="swiper-container" ref = "swiper">
    <div class="swiper-wrapper">
      <slot></slot>
    </div>
        <!-- 如果需要分页器 -->
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import Swiper from 'swiper/swiper-bundle.js'
import 'swiper/swiper-bundle.css'
export default {
  name: 'Swiper',
  props: {
    autoplay: {
      type: Number,
      default: 0
    },
    loop: {
      type: Boolean,
      default: true
    }
  },
  mounted () {
    /* eslint-disable */
    var mySwiper = new Swiper(this.$refs.swiper, {
      loop: this.loop, // 循环模式选项
      autoplay: this.autoplay ? {
        delay: 3000,
        stopOnLastSlide: false,
        disableOnInteraction: true,
      } : false,
      // 如果需要分页器
      pagination: {
        el: '.swiper-pagination'
      },
    })
    /* eslint-disable */
  }
}
</script>

<style lang="scss">
    body{
    background: #ccc;
    }
    .swiper-pagination-bullet {
        opacity: 1;
        vertical-align: middle;
        width: 6px;
        height: 6px;
        border-radius: 50%;
        background-color: hsla(0, 0%, 100%, 0.7);
    }

    .swiper-pagination-bullet-active {
        width: 20px;
        height: 10px;
        background: url("../../assets/icon/dot.png") no-repeat;
        background-size: 100%;
    }
    .swiper-container {
        width: 100%px;
        height: 200px;
    }
</style>