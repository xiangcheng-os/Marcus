<template>
  <div class="product">
    <product-param>
      <template v-slot:buy>
        <button class="btn">立即购买</button>
      </template>
    </product-param>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
    <div class="cc">123</div>
  </div>
</template>

<script>
import ProductParam from './../components/ProductParam'
export default {
  name:'product',
  components:{
    ProductParam
  }

}
</script>

<style lang="scss">
.product{
  button{
    margin-left:20px;
  }
  .cc{
    height: 100px;
  }
}

</style>