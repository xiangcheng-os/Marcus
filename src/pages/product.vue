<template>
  <div class="product">
    <product-param :title="product.name">
      <template v-slot:buy>
        <button class="btn" @click="buy">立即购买</button>
      </template>
    </product-param>
    <div class="content">
      <div class="item-bg">
        <h2>{{product.name}}</h2>
        <h3>{{product.subtitle}}</h3>
        <p>
          <a href="" id="">全球首款双频 GP</a>
          <span>|</span>
          <a href="" id="">骁龙845</a>
          <span>|</span>
          <a href="" id="">AI 变焦双摄</a>
          <span>|</span>
          <a href="" id="">红外人脸识别</a>
        </p> 
        <div class="price">
          <span>￥<em>{{product.price}}</em></span>
        </div>
      </div>
      <div class="item-bg-2"></div>
      <div class="item-bg-3"></div>
      <div class="item-swiper">
        <swiper :options="swiperOption">
          <swiper-slide><img src="/imgs/product/gallery-2.png" alt=""></swiper-slide>
          <swiper-slide><img src="/imgs/product/gallery-3.png" alt=""></swiper-slide>
          <swiper-slide><img src="/imgs/product/gallery-4.png" alt=""></swiper-slide>
          <swiper-slide><img src="/imgs/product/gallery-5.jpg" alt=""></swiper-slide>
          <swiper-slide><img src="/imgs/product/gallery-6.jpg" alt=""></swiper-slide>
          <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
        <p class="desc">小米8 AI变焦双摄拍摄</p>
      </div>
      <div class="item-video">
        <h2>60帧超慢动作摄影<br/>慢慢回味每一瞬间的精彩</h2>
        <p>后置960帧电影般超慢动作视频，将眨眼间的美妙展现的淋漓尽致!<br/>更能AI 精准分析视频内容，15个场景智能匹配背景音效</p>
        <div class="video-bg"  @click="showSlide='slideDown'"></div>
        <div class="video-box" v-show="showSlide">
          <div class="overlay" v-if="showSlide"></div>
          <div class="video" :class="showSlide">
            <span class="icon-close" @click="closeVideo"></span>
            <video src="/imgs/product/video.mp4" muted autoplay controls="controls"></video>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ProductParam from './../components/ProductParam'
import { swiper,swiperSlide } from 'vue-awesome-swiper'
export default {
  name:'product',
  components:{
    ProductParam,
    swiper,
    swiperSlide
  },
  data(){
    return{
      product:{},//商品信息
      showSlide:'',//控制动画效果
      swiperOption:{
        autoplay:true,
        slidesPerView:3,
        spaceBetween:30,
        freeMode:true,
        pagination:{
          el:'.swiper-pagination',
          clickable: true,
        }

      }
    }
  },
  mounted(){
    this.getProductInfo();
  },
  methods:{
    getProductInfo(){
      let id = this.$route.params.id;
      this.axios.get(`/products/${id}`).then((res)=>{
        this.product = res;
      })
    },
    buy(){
      let id = this.$route.params.id;
      this.$router.push(`/detail/${id}`)
    },
    closeVideo(){
      this.showSlide='slideUp';
      setTimeout(()=>{
        this.showSlide='';
      },600)
    }
  }

}
</script>

<style lang="scss">
@import './../assets/scss/mixin.scss';
.product{
  .content{
    .item-bg{
      background:url('/imgs/product/product-bg-1.png') no-repeat center;//背景图不重复切居中
      height:718px;
      text-align: center;//元素文本水平居中
      h2{
        font-size: 80px;//字体大小
        padding-top:55px;//元素上内边距
      }
      h3{
        font-size: 24px;
        letter-spacing: 10px;//字母间距
      }
      p{
        margin-top: 21px;//元素上外边距
        margin-bottom: 40px;//元素下外边距
        a{
          font-size:16px;
          color:#333;
        }
        span{
          margin: 0 15px;
        }
      }
      .price{
        font-size: 30px;
        color: #333;
        em{
          font-style: normal;
          font-size: 38px;
        }
      }
    }
    .item-bg-2{
      background:url('/imgs/product/product-bg-2.png') no-repeat center;
      height: 480px;
      background-size:1226px 397px;//背景图尺寸
    }
    .item-bg-3{
      background: url('/imgs/product/product-bg-3.png') no-repeat center;
      height: 638px;
      background-size: cover;//背景图完全覆盖背景区域
    }
    .item-swiper{
      margin:36px auto 52px;
      .desc{
        font-size:18px;
        color:#333;
        text-align:center;//文本对齐方式
      }
      img{
        width: 100%;
      }
    }
    .item-video{
      height: 1044px;
      background-color: #070708;
      margin-bottom: 76px;
      color:#fff;
      text-align: center;
      h2{
        font-size:60px;
        padding-top: 82px;
        margin-bottom: 47px;
      }
      p{
        font-size:24px;
        margin-bottom: 58px;
      }
      .video-bg{
        background:url('/imgs/product/gallery-1.png') no-repeat center;
        background-size:cover;
        width: 1226px;
        height: 540px;
        margin: 0 auto 120px;
        cursor: pointer;//鼠标变成手

      }
      .video-box{
        .overlay{
          @include position(fixed);
          background-color: #333;
          opacity: .4;//设置元素的不透明级别
          z-index:10;//设置元素的堆叠顺序
        }
        //使元素向下移动
        @keyframes slideDown{
          from{
            top:-50%;
            opacity: 0;
          }
          to{
            top:50%;
            opacity: 1;
          }
        }
        @keyframes slideUp{
          from{
            top: 50%;
            opacity: 1;
          }
          to{
            top:-50%;
            opacity: 0;
          }
        }
        .video{
          position: fixed;//基于浏览器窗口 浮动与文档流之上，随着滚动一直停留在屏幕之中
          top:-50%;
          left:50%;
          transform: translate(-50%,-50%);//定义2D转换
          z-index: 10;
          width: 1000px;
          height: 536px;
          opacity: 1;//透明度
          
          // &表示当前元素
          // a{
          //   &.b{}
          // } 
          // 编译之后就是 a.b{}
          &.slideDown{
            //animation 使动画和div绑定
            animation:slideDown .6s linear;
            top:50%;
          }
          &.slideUp{
            animation:slideUp .6s linear;
          }
          .icon-close{
            position: absolute;
            top: 20px;
            right: 20px;
            @include bgImg(20px,20px,'/imgs/icon-close.png');
            //@include 指令可以将混入（mixin）引入到文档中。
            //@mixin 指令允许我们定义一个可以在整个样式表中重复使用的样式

            cursor:pointer;
            z-index: 11;

          }

          video{
            width: 100%;
            height: 100%;
            object-fit: cover;//指定可替换元素的内容应该如何适应到其使用的高度和宽度确定的框
            outline: none;//边框样式
          }
      }     
     }
    }
  }
  button{
    margin-left:20px;
  }
}

</style>