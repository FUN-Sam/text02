<template>
  <div class="recommend">
    <!-- 轮播图区域 -->
    <Banner swiperid="mybanner1" goTo="toLeft">
      <div slot="swiper-con" class="swiper-slide">
        <img src="../assets/images/home/img01.png" alt />
      </div>
      <div slot="swiper-con" class="swiper-slide">
        <img src="../assets/images/home/img02.jpg" alt />
      </div>
      <div slot="swiper-con" class="swiper-slide">
        <img src="../assets/images/home/img03.png" alt />
      </div>
      <div slot="swiper-con" class="swiper-slide">
        <img src="../assets/images/home/img04.jpg" alt />
      </div>
      <div slot="swiper-con" class="swiper-slide">
        <img src="../assets/images/home/img05.jpg" alt />
      </div>
    </Banner>
    <!-- 导航区域 -->
    <ul class="ul-nav">
      <li v-for="(item,index) in arr" :key="index">
        <img :src="item.url" alt class="mypic" />
        <span class="smalltitle">{{item.smalltitle}}</span>
        <br />
        <span>{{item.title}}</span>
      </li>
    </ul>
    <!-- 大图区域 -->
    <div class="nav-img">
      <img src="../assets/images/home/banner.png" alt class="banner" />
      <div class="linghang">
        <span>
          <img src="../assets/images/home/linghang.jpg" alt />
        </span>
        <span>领航装饰</span>
      </div>
      <span class="design">专注家装设计 口碑保障</span>
    </div>
    <!-- 深圳找装修区域 -->
    <div class="search-renovate">
      <ul class="search-renovate-h">
        <li class="search-renovate-t">
          <h3>深圳找装修</h3>
        </li>
        <li class="search-renovate-m">
          <span>百万业主口碑装修公司</span>
        </li>
        <li>
          <a href="#" class="more">更多></a>
        </li>
      </ul>
      <ul class="renovatelist">
        <li v-for="(item,index) in renovatearr" :key="index">
          <img :src="item.url" alt class="renovate-pic" />
          <br />
          <p class="renovate-title">{{item.title}}</p>
          <span class="iconfont icon-start-copy" style="color:red"></span>
          <br />
          <span class="service">{{item.service}}</span>
        </li>
      </ul>
      <div class="coupon">
        <p>装修有好券</p>
        <ul>
          <li v-for="(item,index) in couponarr" :key="index">
            <div class="coupon-left">
              <div class="coupon-top">
                <span>￥</span>
                <span class="aboutprice">{{item.price}}</span>
                <span class="use">{{item.use}}</span>
              </div>
              <div class="coupon-bottom">
                <span>{{item.validity}}</span>
              </div>
            </div>
            <div class="coupon-right">
              <span>{{item.getcoupon}}</span>
            </div>
          </li>
        </ul>
      </div>
      <div class="goodservice">
        <p>装修好服务</p>
        <ul>
          <li v-for="(item,index) in goodservicearr" :key="index">
            <img :src="item.url" alt class="imgbg" />
            <h4>{{item.p1}}</h4>
            <span class="service-design">{{item.p2}}</span>
          </li>
        </ul>
      </div>
    </div>
    <!-- 深圳买建材区域 -->
    <div class="search-renovate">
      <ul class="search-renovate-h">
        <li class="search-renovate-t">
          <h3 style="color:rgba(239, 78, 78)">深圳买建材</h3>
        </li>
        <li class="search-renovate-m">
          <span>
            <a href="#">查口碑</a>
            <a href="#">看点评</a>
            <a href="#">享优惠</a>
          </span>
        </li>
        <li>
          <a href="#" class="more">更多></a>
        </li>
      </ul>
      <ul class="renovate-material">
        <li
          v-bind:class="{liactive:active==index}"
          @click="clickmaterial(index,item)"
          v-for="(item,index) in arr"
          :key="index"
        >{{item}}</li>
      </ul>
      <div>
        <i class="iconfont icon-shanglajiantou" v-show="ishow" @click="pickup"></i>
        <i class="iconfont icon-xialasanjiao" v-show="!ishow" @click="show"></i>
      </div>
      <!-- 深圳买建材橱柜对应渲染的数据 -->
      <ul class="renovatelist buymaterial">
        <li v-for="(item,index) in buymateriallist" :key="index">
          <img :src="item.url" alt class="renovate-pic" />
          <br />
          <p class="renovate-title">{{item.title}}</p>
          <span class="iconfont icon-start-copy" style="color:red"></span>
          <br />
          <span class="num">
            口碑值:
            <span style="color:rgba(254, 62, 45)">{{item.num}}</span>
          </span>
          <br />
          <span class="service">{{item.service}}</span>
        </li>
      </ul>
      <!-- 深圳居家服务对应的渲染的数据 -->
      <ul class="renovatelist buymaterial">
        <li v-for="(item,index) in housingarr" :key="index">
          <img :src="item.url" alt class="renovate-pic" />
          <br />
          <p class="renovate-title">{{item.title}}</p>
          <span class="iconfont icon-start-copy" style="color:red"></span>
          <br />
          <span class="num">
            口碑值:
            <span style="color:rgba(254, 62, 45)">{{item.num}}</span>
          </span>
          <br />
          <span class="service">{{item.service}}</span>
        </li>
      </ul>
      <!-- 深圳瓷砖的渲染数据 -->
      <ul class="renovatelist buymaterial">
        <li v-for="(item,index) in brickarr" :key="index">
          <img :src="item.url" alt class="renovate-pic" />
          <br />
          <p class="renovate-title">{{item.title}}</p>
          <span class="iconfont icon-start-copy" style="color:red"></span>
          <br />
          <span class="num">
            口碑值:
            <span style="color:rgba(254, 62, 45)">{{item.num}}</span>
          </span>
          <br />
          <span class="service">{{item.service}}</span>
        </li>
      </ul>
    </div>
    <!-- 精选品牌区域 -->
    <div class="search-renovate">
      <ul class="search-renovate-h">
        <li class="search-renovate-t">
          <h3 style="color:rgba(124, 89, 224)">精选品牌</h3>
        </li>
        <li>
          <a href="#" class="more">深度解读更多大牌></a>
        </li>
      </ul>
      <ul class="brand">
        <li>
          <img src="../assets/images/home/sfy.png" alt />
        </li>
        <li>
          <span>齐家优选品牌推荐</span>
          <span>全家2000+线下实体门店</span>
        </li>
        <li class="gotosee">去看看</li>
      </ul>
    </div>
    <!-- 装修灵感 -->
    <div class="search-renovate">
      <ul class="search-renovate-h">
        <li class="search-renovate-t">
          <h3 style="color:rgba(15, 170, 121)">装修灵感</h3>
        </li>
        <li class="search-renovate-m">
          <span>海量装修效果图</span>
        </li>
        <li>
          <a href="#" class="more">寻找家的感觉></a>
        </li>
      </ul>
      <ul class="nav-list">
        <!-- 效果图   案例 日记 -->
        <li
          v-bind:class="{actives:active==index}"
          @click="change(index,item.name)"
          v-for="(item,index) in navarr"
          :key="index"
        >{{item.name}}</li>
      </ul>
      <div>
        <!-- 风格  户型  -->
        <ul class="stylelist">
          <li
            v-bind:class="{sactive:active==index}"
            v-for="(item,index) in descarr"
            :key="index"
          >{{item.name}}</li>
        </ul>
        <ul class="stylelist">
          <li
            v-bind:class="{sactive:active==index}"
            v-for="(item,index) in casearr"
            :key="index"
          >{{item.name}}</li>
        </ul>
      </div>
      <!-- 风格的展示 -->
      <ul class="style-display">
        <li v-for="(item,index) in stylearr" :key="index">
          <img :src="item.imgSrc" alt />
          <span class="styles" v-bind:style="{color:item.color}">{{item.finishStyle}}</span>
          <span class="count">{{item.quantity}}</span>
        </li>
      </ul>
      <!-- 户型的展示 -->
      <ul class="style-display apartment">
        <li v-for="(item,index) in apartment" :key="index">
          <img :src="item.imgSrc" alt />
          <span class="styles" v-bind:style="{color:item.color}">{{item.finishStyle}}</span>
          <span class="count">{{item.quantity}}</span>
        </li>
      </ul>
      <!-- 案例的综合展示 -->
      <ul class="style-display case">
        <li v-for="(item,index) in casepic" :key="index">
          <img :src="item.imgSrc" alt />
          <span class="styles" v-bind:style="{color:item.color}">{{item.finishStyle}}</span>
          <span class="desc">{{item.title}}</span>
        </li>
      </ul>
      <!-- 案例的现代展示 -->
      <ul class="style-display case">
        <li v-for="(item,index) in stylepicarr" :key="index">
          <img :src="item.imgSrc" alt />
          <span class="styles">{{item.finishStyle}}</span>
          <span class="desc">{{item.title}}</span>
        </li>
      </ul>
      <!-- 日记的展示 -->
      <ul class="diray">
        <li v-for="(item,index) in  diaryarr" :key="index">
          <img :src="item.imgsrc" alt />
          <h4 class="desc">{{item.title}}</h4>
          <div>
            <img :src="item.person" alt class="person" />
            <span>
              {{item.desc}}/
              <span style="color:rgba(183, 183, 183)">{{item.num}}/{{item.style}}</span>
            </span>
          </div>
        </li>
      </ul>
      <p class="searchmore">
        <a href="#">查看更多屋主装修过程></a>
      </p>
      <!-- 获取报价 -->
      <div>
        <p>在深圳，把家装成这样要花多少钱？</p>
        <ul class="getprice">
          <li>
            <img src="../assets/images/home/jiuanqi.png" alt />
          </li>
          <li class="price-right">
            <div class="top">
              <input type="text" placeholder="房屋面积" />
              <input type="text" placeholder="2室1厅1厨1卫" />
            </div>
            <div class="bottom">
              <button>获取报价</button>
            </div>
          </li>
        </ul>
      </div>
    </div>
    <!-- 装修干货区域 -->
    <div class="search-renovate">
      <ul class="search-renovate-h">
        <li class="search-renovate-t">
          <h3 style="color:rgba(77, 124, 226)">装修干货</h3>
        </li>
        <li class="search-renovate-m">
          <span>百万装友跳出的好内容</span>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
import Banner from "../components/Banner.vue";

export default {
  name: "recommend",
  components: {
    Banner
  },
  data: function() {
    return {
      active: 0, //当前索引
      currentView: "", //买建材对应要显示的内容
      ishow: false, //箭头和剩下的建材的是否显示
      arr: [],
      renovatearr: [],
      couponarr: [],
      goodservicearr: [],
      renovatematerialarr: [],
      splicearr: [],
      buymateriallist: [],
      housingarr: [],
      brickarr: [],
      stylearr: [],
      navarr: [],
      apartment: [],
      casearr: [],
      descarr: [],
      casepic: [],
      diaryarr: [],
      stylepicarr: [],
      arr: []
    };
  },
  mounted() {
    //请求index的数据
    this.getindexdata();
  },
  methods: {
    getindexdata() {
      console.log("bbb");
      this.$axios.get("/data/home/index.json").then(res => {
        //   let obj = {
        //     list1:[],
        //     list2:[],
        //     list3:[],
        //   }
        // let {list1,list2,list3} = obj
        // let [a,b,c] = [1,2,3]
        this.arr = res.data.mydata.lists;
        this.renovatearr = res.data.mydata.renovate;
        this.couponarr = res.data.mydata.coupon;
        this.goodservicearr = res.data.mydata.goodservice;
        this.renovatematerialarr = res.data.mydata.renovatematerial;
        this.buymateriallist = res.data.mydata.buymateriallist;
        this.housingarr = res.data.mydata.houseservice;
        this.brickarr = res.data.mydata.brick;
        this.stylearr = res.data.mydata.style.stylepic;
        this.navarr = res.data.mydata.nav;
        this.apartment = res.data.mydata.apartment;
        this.casearr = res.data.mydata.case.title;
        this.casepic = res.data.mydata.case.casepics;
        this.stylepicarr = res.data.mydata.case.stylepics;
        this.descarr = res.data.mydata.style.desc;
        this.diaryarr = res.data.mydata.case.diray;

        let arr = this.renovatematerialarr.filter((item, i) => {
          return i < 8;
        });
        this.arr = arr;
        console.log("arr", arr);
      });
    },
    //点击买建材对应的选项
    clickmaterial(i, v) {
      console.log("点击选建材", i, v);
      this.active = i;
    },
    pickup() {
      console.log("收起来");
      //点击上拉的时候下拉箭头显示  收起箭头消失
      //点击上拉的时候 只显示前10个
      let arr = this.renovatematerialarr.filter((item, i) => {
        return i < 8;
      });
      this.arr = arr;
      this.ishow = false;
    },
    show() {
      console.log("下拉显示出来");
      //点击下拉的时候 下拉箭头消失  收起箭头显示
      //点击下来的时候 整个数组显示出来
      this.ishow = true;
      this.arr = this.renovatematerialarr;
      // this.renovatematerialarr.push(this.splicearr );
    },
    change(index, item) {
      console.log("已经改变了", item, index);
      this.active = index;
    }
  }
};
</script>
<style lang="less">
@import url("../assets/css/font/iconfont.css");
@import url("../assets/css/recommend/recommend.css");
</style>