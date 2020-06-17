<template>
  <div class="footer">
    <div class="footer-logo">
      <img src="/imgs/logo-footer.png" alt="">
      <p>小米商城</p>
    </div>
    <div class="footer-link">
      <a href="">小米真香</a><span>|</span>
      <a href="">华为可以</a><span>|</span>
      <a href="">苹果也行</a><span>|</span>
      <a href="">三星就算了</a><span>|</span>
      <a href="">锤子加油</a><span>|</span>
    </div>
    <div class="copyright">京公网安备11000002000001号</div>
  </div>
</template>

<script>
export default {
  name:'nav-footer'

}
</script>

<style lang="scss">
  .footer{
    height: 234px;
    border-top: 4px solid #ff6600;
    background-color: #333;
    color: #999;
    font-size: 16px;
    text-align: center;
    .footer-logo{
      margin-top: 46px;
      margin-bottom: 31px;
      img{
        width: 53px;
        height: 36px;
        margin-bottom: 13px;
      }
    }
    .footer-link{
      a{
        color: #999;
        display: inline-block;
      }
      span{
        margin: 0 10px;
      }
    }
  }

</style>