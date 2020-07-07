<template>
  <div class="detail">
    <product-param :title="product.name"></product-param>
    <div class="wrapper">
      <!-- clearfix 清除浮动 -->
      <div class="container clearfix">
        <div class="swiper">
            <swiper :options="swiperOption">
            <swiper-slide><img src="/imgs/detail/phone-1.jpg" alt=""></swiper-slide>
            <swiper-slide><img src="/imgs/detail/phone-2.jpg" alt=""></swiper-slide>
            <swiper-slide><img src="/imgs/detail/phone-3.jpg" alt=""></swiper-slide>
            <swiper-slide><img src="/imgs/detail/phone-4.jpg" alt=""></swiper-slide>
            <div class="swiper-pagination" slot="pagination"></div>
          </swiper>
        </div>
        <div class="content">
          <h2 class="item-title">{{product.name}}</h2>
          <p class="item-info">相机全新升级 / 960帧超慢动作/ 手持超级夜景 / 全球首款双频GPS / 骁龙845处理器 / 红<br/>外人脸解锁 / AI变焦双摄 / 三星 AMOLED 屏</p>
          <div class="delivery">小米自营</div>
          <div class="item-price">{{product.price}}元 <span class="del">1999元</span></div>
          <div class="line"></div>
          <div class="item-addr">
            <i class="icon-loc"></i>
            <div class="addr">北京 北京市 朝阳区 安定门街道</div>
            <div class="stock">有现货</div>
          </div>
          <div class="item-version clearfix">
            <h2>选择版本</h2>
            <div class="phone fl" :class="{'checked':version==1}" @click="version=1">6GB+64GB 全网通</div>
            <div class="phone fr" :class="{'checked':version==2}" @click="version=2">4G+64GB 移动4G</div>
          </div>
          <div class="item-color">
            <h2>选择颜色</h2>
            <div class="phone checked">
              <span class="color"></span>
              深空灰
            </div>
          </div>
          <div class="item-total">
            <div class="phone-info clearfix">
              <div class="fl">{{product.name}} {{version==1?'6GB+64GB 全网通':'4GB+64GB 移动4G'}} 深灰色</div>
              <div class="fr">{{product.price}}元</div>
            </div>
            <div class="phone-total">总计：{{product.price}} 元</div>
          </div>
          <div class="btn-group">
            <a href="javascript:;" class="btn btn-huge fl" @click="addCart">加入购物车</a>
          </div>
        </div>
      </div>
    </div>
    <div class="price-info">
      <div class="container">
        <h2>价格说明</h2>
        <div class="desc">
          <img src="/imgs/detail/item-price.jpeg" alt="">
        </div>
      </div>
    </div>
    <service-bar></service-bar>
  </div>
</template>

<script>
import { swiper, swiperSlide } from 'vue-awesome-swiper'
import ProductParam from './../components/ProductParam'
import ServiceBar from './../components/ServiceBar'
export default {
  name:'detail',
  data(){
    return{
      id:this.$route.params.id,//获取商品ID
      err:'',
      version:1,//商品版本切换
      product:{},//商品信息
      swiperOption:{
        autoplay:true,
        pagination:{
          el:'.swiper-pagination',
          clickable:true,
        }
      }  
    }
  },
  //组件
  components:{
    swiper,
    swiperSlide,
    ProductParam,
    ServiceBar
  },
  //钩子  页面初始化完成，再对dom进行渲染
  mounted(){
    this.getProductInfo();
  },
  //methods属性是定义方法的主要区域，在此属性中，可以定义各种自定义行数名的方法以及参数
  methods:{
    getProductInfo(){
      this.axios.get(`/products/${this.id}`).then((res)=>{
        this.product = res;
      })
    },
    addCart(){
      this.axios.post('/carts',{
        productId:this.id,
        selected:true
      }).then((res={cartProductVoList:0})=>{
        this.$store.dispatch('saveCartCount',res.cartTotalQuantity);
      })
    }
  }

}
</script>

<style lang="scss">
  @import './../assets/scss/config.scss';
  @import './../assets/scss/mixin.scss';
  .detail{
    .wrapper{
      .swiper{
        float: left;
        width:642px;
        height: 617px;
        margin-top:5px;
        img{
          width: 100%;
          height: 100%;
        }
      }
      .content{
        float: right;
        width: 584px;
        height: 870px;
        .item-title{
          font-size: 28px;
          padding-top:30px;//元素上内边距
          padding-bottom: 16px;
          height: 26px;
        }
        .item-info{
          font-size: 14px;
          height: 36px;
        }
        .delivery{
          font-size: 16px;
          color:#ff6700;
          margin-top: 26px;
          margin-bottom: 14px;
          height: 15px;
        }
        .item-price{
          font-size: 20px;
          color:#ff6700;
          height: 19px;
          .del{
            font-size: 16px;
            color:#999999;
            margin-left:10px;
            text-decoration:line-through;
          }
        }
        .line{
          height: 0;
          margin-top: 25px;
          margin-bottom: 28px;
          border-top:1px solid #e5e5e5;
        }
        .item-addr{
          height: 108px;
          background-color: #fafafa;
          border:1px solid #e5e5e5;
          box-sizing: border-box;
          padding-top: 31px;//元素上内边距
          padding-left: 64px;//元素左内边距
          font-size: 14px;
          line-height: 14px;
          position: relative;//相对定位
          .icon-loc{
            position: absolute;//绝对定位
            top: 27px;
            left:34px;
            @include bgImg(20px,20px,'/imgs/detail/icon-loc.png');
          }
          .addr{
            color: #666;
          }
          .stock{
            margin-top: 15px;//元素上外边距
            color: #ff6700;
          }
        }
        .item-version,.item-color{
          margin-top: 30px;
          h2{
            font-size: 18px;
            margin-bottom: 20px;
          }
          
        }
        .item-version,.item-color{
          .phone{
            width: 287px;
            height: 50px;
            line-height: 50px;
            font-size: 16px;
            color:#333;
            border:1px solid #e5e5e5;
            box-sizing: border-box;//不用考虑边框和内边距
            text-align:center;
            cursor:pointer;
            span{
              color:#666;
              margin-left: 15px;
            }
            .color{
              display:inline-block;//不独占一行的块元素
              width: 14px;
              height: 14px;
              background-color: #666;
            }
            &.checked{
              border:1px solid #ff6600;
              color:#ff6600;
            }
          }
        }
       .item-total{
         height: 108px;
         background: #fafafa;
         padding:24px 33px 29x 30px;
         font-size: 14px;
         margin-top: 50px;
         margin-bottom: 30px;
         box-sizing: border-box;
         .phone-total{
           font-size: 24px;
           color: #ff6600;
           margin-top: 18px;
         }
       } 
      }
    }
    .price-info{
      background-color: #f3f3f3;
      height: 340px;
      h2{
        font-style: 24px;
        color: #333;
        padding-top: 38px;
        margin-bottom: 30px;
      }
    }
  }

</style>