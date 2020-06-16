<template>
  <div class="header">
    <div class="nav-topbar">
      <div class="container">
        <div class="topbar-menu">
          <a href="javascript:;">小米商城</a>
          <a href="javascript:;">MUI</a>
          <a href="javascript:;">云服务</a>
          <a href="javascript:;">协议规则</a>
        </div>
        <div class="topbar-user">
          <a href="javascript:;">登陆</a>
          <a href="javascript:;">注册</a>
          <a href="javascript:;" class="my-cart"><span class="icon-cart"></span>购物车</a>
        </div>
      </div>
    </div>
    <div class="nav-header">
      <div class="container">
        <div class="header-logo">
          <a href="/#/index"></a>
        </div>
        <!-- <div class="header-menu">
          <span>小米手机</span>
          <div class="children"></div>
        </div>
        <div class="header-menu">
          <span>小米手机</span>
          <div class="children"></div>
        <div class="header-menu">
          <span>小米手机</span>
          <div class="children"></div> -->
        </div>
      <div class="header-search"></div>
    </div>
  </div>
</template>

<script>
export default {
  name:'nav-header'

}
</script>

<style lang="scss">
  @import './../assets/scss/base.scss';
  .header{
    .nav-topbar{
      height: 39px;
      line-height: 39px;
      background-color: #333;
      color: #B0B0B0;
      .container{
      width: 1226px;
      margin-right: auto;
      margin-left: auto;
      display: flex;
      justify-content:space-between;
      align-items: center;
      a{
        display: inline-block;
        color:#B0B0B0;
        margin-right: 17px;
      }
      .my-cart{
        width: 100px;
        background-color: #ff6600;
        text-align: center;
        color: #fff;
        margin-right: 0;
        .icon-cart{
          display: inline-block;
          width: 16px;
          height: 12px;

          background: url('/imgs/icon-cart-checked.png') no-repeat center;
          background-size:contain;
          margin-right: 4px;
        }
      }
     }
    }
    .nav-header{
      .header-logo{
        display: inline-block;
        width: 55px;
        height: 55px;
       
      }
      .header-menu{
        display: inline-block;
        width: 209px;
        padding-left: 209px;
        .item-menu{
          display: inline-block;
          color: #333;
          font-weight: bold;
          font-size: 16px;

        }
      }
    }
    
  }

</style>