<template>
  <div>
    <div>
      <order-header></order-header>
    </div>
    <service-bar></service-bar>
    
  </div>
  
</template>

<script>
import Orderheader from './../components/OrderHeader'
import ServiceBar from './../components/ServiceBar'
export default {
  name:'cart',
  data(){

  },

  components:{
    Orderheader,
    ServiceBar

  }


}
</script>

<style>

</style>