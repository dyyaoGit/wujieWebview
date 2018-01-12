<template>
  <div class="main-content">
    <ul class="side-bar">
      <li v-for="(item, index) in res" class="sidebar-item" :class="{'is-active': level1 == index}" @click="level1 = index"> <!--1级-->
          <div class="num">{{index+1}}</div>
          <div class="type">
            <div class="type-title">
              {{item.name}}
            </div>
            <div class="desc">
              SKIN CARE COSMETIC
            </div>
          </div>
      </li>
    </ul>
    <ul class="content" v-for="(level, index) in res" v-show="level1 === index">
      <li class="content-item" v-for="item in level.children">  <!--2级-->
        <h2 class="content-item-title">
          <div>{{item.name}}</div>
          <div class="little-title">SKIN CARE</div>
        </h2>
        <div class="shop-wrap">
          <div class="shop-item" v-for="val in item.children"> <!--3级-->
            <div class="shop-item-img">
              <img :src="val.img">
            </div>
            <div class="shop-desc">
              {{val.name}}
            </div>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
  import axios from 'axios'
export default {
  name: 'main-content',
  data () {
    return {
      level1: 0,
      level2: 2,
      level3: 3,
      res: []
    }
  },
  created() {
    axios.get('http://yly3.ylyedu.com/index/index/cat').then(res => {
      this.res = res.data.data;
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
  .main-content {
    display: flex;
    /*justify-content: space-between;*/
    font-size: 24px;
  }
  .side-bar {
    display: flex;
    flex-direction: column;
    justify-content: start;
    background: #fff;
    width: 2.4rem;
    max-height: 12.12rem;
    overflow: scroll;
    overflow-scrolling: touch;
    -webkit-overflow-scrolling: touch;
    /*height: 11.84rem;*/
  }
  .sidebar-item {
    flex-shrink: 0;
    display: flex;
    padding: .27rem .33rem 0 .14rem;
    width: 2.4rem;
    height: 2.02rem;
    box-sizing: border-box;
    font-family: PingFangSC-Medium;
    color: #2D313B;
    font-size: 15px;
    background: #F3F3F3;
  }
  .sidebar-item .type {
    margin-left: .14rem;
  }
  .type .type-title {
    margin-bottom: .06rem;
    font-family: PingFangSC-Medium;
    font-weight: 600;
    line-height: .42rem;
    font-size: 15px;
  }
  .sidebar-item .num {
    width: .28rem;
    height: .28rem;
    text-align: center;
    line-height: .28rem;
    font-size: 10px;
    color: #fff;
    background: #b9b9b9;
  }
  .sidebar-item .type .desc {
    color: #b9b9b9;
  }
  .sidebar-item .desc {
    width: 1.2rem;
    line-height: .2rem;
    font-size: 11px;
  }

  .side-bar .is-active {
    background: #fff;
  }
  .side-bar .is-active .num {
    background: #2c323b;
  }
  .content {
    flex-grow: 1;
    max-height: 12.12rem;
    overflow: scroll;
    overflow-scrolling: touch;
    -webkit-overflow-scrolling: touch;
    box-sizing: border-box;
    background: #fff;
  }
  .content-item-title {
    font-family: "PingFangSC-Medium";
    display: flex;
    flex-direction: column;
    justify-content: center;
    width: 4.7rem;
    margin: 0 auto;
    font-weight: 600;
    font-size: 14px;
    line-height: 20px;
    background: #f3f3f3;
    text-align: center;
    height: 1rem;
  }
  .content-item-title .little-title {
    font-family: "PingFangSC-Regular";
    font-weight: 500;
    font-size: 10px;
    line-height: 14px;
  }
  .shop-wrap {
    display: flex;
    flex-wrap: wrap;
  }
  .shop-item {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 1.7rem;
    height: 2.02rem;
    box-sizing: border-box;
    padding: .326rem .45rem 0 .46rem;
  }
  .shop-item-img {
    width: .77rem;
    height: .87rem;
    overflow: hidden;
  }
  .shop-item-img img {
    width: 100%;
    max-height: 100%;
  }
  .shop-desc {
    font-family: PingFangSC-Regular;
    color: #2D313B;
    margin-top: .28rem;
    line-height: .36rem;
    font-size: 13px;

  }
</style>
