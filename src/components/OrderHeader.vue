<template>
  <div class="order-header">
    <div class="container">
      <div class="header-logo">
        <a href="/#/index"></a>
      </div>
      <div class="title">
        <h2>我的购物车<span>温馨提示</span></h2>
      </div>
      <div class="username">
        <a href="javascript:;"></a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'order-header'

}
</script>

<style lang="scss">
.order-header{
  padding: 30px 0;
  .header-logo{
    float:left;
  }
  .title,.username{
    display: inline-block;
    height: 55px;
    line-height: 55px;
  }
  .title{
    font-size: 28px;
    float: left;
    span{
      font-size: 14px;
      margin-left: 17px;
      color: #333;
    }
  }
  .username{
    float: right;
  }
}

</style>