<template>
    <header class="index-header">
      <a href="mine.html?cpid=0">
        <div class="header-user">
          <div class="user-btn"></div>
        </div>
      </a>
      <div class="header-logo"></div>
      <div class="header-search" @click = "goSearch"></div>
    </header>
</template>

<script>
export default {
  name: 'indexHeader',
  methods: {
    goSearch () {
      this.$router.push('/search')
    }
  }
}
</script>

<style lang='scss' scoped>
@import "~@/assets/style/mixins.scss";
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
    .user-btn{
    width: 25px;
    height: 25px;
    background: url(~@/assets/icon/user-btn.png);
    background-size: 100%;
  }
</style>
