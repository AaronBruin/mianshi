<template>
  <div class="swiper" @mouseover="overHd" @mouseout="auto">
    <div class="swiper-item" v-for="(item,ind) in gallery" :key="item.img" v-show="ind==index">
      <img :src="item.img" width="100%">
    </div>
    <div class="thumbs">
      <span class="line_left" @click="moveLeft"></span>
      <span class="thumb" :class="{'active' :item==index+1}" v-for="item in 3" :key='item'
        @click="index=item-1">{{gallery[Number(item)- 1].title}}
        <span :class="{'line' :item==index+1}"></span></span>
      <span class="line_right" @click="moveRight"></span>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      gallery: {
        type: Array,
        default () {
          return []
        }
      }
    },
    data() {
      return {
        //默认显示
        index: 0,
        stopID: null,
      }
    },
    // 当组件挂载完毕 执行自动播放
    created() {
      this.auto();
    },
    methods: {
      //鼠标一开  auto自动执行
      auto() {
        this.stopID = setInterval(() => {
          this.index++;
          this.check();
        }, 2000)
      },
      overHd() {
        clearInterval(this.stopID);
      },
      //检查边界
      check() {
        if (this.index == this.gallery.length) {
          this.index = 0;
        }
      },
      moveLeft() {
        if (this.index == 0) {
          this.index = this.gallery.length - 1
        } else {
          this.index = this.index - 1
        }
      },
      moveRight() {
        if (this.index + 1 >= this.gallery.length) {
          this.index = 0
        } else {
          this.index = this.index + 1
        }
      },
    }
  }
</script>

<style lang="scss" scoped="scoped">
  .swiper {
    position: relative;
  }

  .swiper-item {
    width: 100%;
    height: 479px;

    img {
      width: 100%;
      height: 100%;
    }
  }

  .swiper .thumbs {
    position: absolute;
    bottom: 0px;
    width: 1200px;
    height: 50px;
    left: calc(50% - 600px);
    display: flex;
    align-items: center;
    text-align: center;
  }

  .thumb {
    flex: 1;
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    height: 50px;
    color: #4a596f;
    font-size: 16px;
    transition: all 200ms;
    // display: inline-block;
    background-color: rgba(255, 255, 255, 0.8);
    border-right: 1px solid rgba(255, 255, 255, 0.6) !important;
  }

  .thumb:hover {
    cursor: pointer;
    color: #009cff;
  }

  .active {
    color: #009cff;
    height: 50px;
    font-size: 16px;
    // border-bottom: 4px solid #009cff;
  }

  .line::after {
    content: "";
    width: 100%;
    height: 4px;
    background-color: #009cff;
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
  }

  .line_left {
    position: relative;
    width: 50px;
    height: 50px;
    border-top-left-radius: 10px;
    background-color: rgba(255, 255, 255, 0.8);
    border-right: 1px solid rgba(255, 255, 255, 0.6) !important;
  }

  .line_left::before {
    content: " ";
    display: inline-block;
    height: 18px;
    width: 18px;
    border-width: 0 0 4px 4px;
    border-color: #b2bac4;
    border-style: solid;
    -webkit-transform: matrix(.51, .51, -0.51, .51, 0, 0);
    transform: matrix(.51, .51, -0.51, .51, 0, 0);
    position: absolute;
    top: calc(50% - 8px);
    left: calc(50% - 8px);
  }

  .line_right {
    position: relative;
    width: 50px;
    height: 50px;
    border-top-right-radius: 10px;
    background-color: rgba(255, 255, 255, 0.8);
    border-right: 1px solid rgba(255, 255, 255, 0.6) !important;
  }
  .line_right::before {
    content: " ";
    display: inline-block;
    height: 18px;
    width: 18px;
    border-width: 4px 4px 0 0;
    border-color: #b2bac4;
    border-style: solid;
    -webkit-transform: matrix(.51, .51, -0.51, .51, 0, 0);
    transform: matrix(.51, .51, -0.51, .51, 0, 0);
    position: absolute;
    top: calc(50% - 8px);
    right: calc(50% - 8px);
  }
  .line_left:hover{
    background-color:#ffffff;
  }
  .line_right:hover{
    background-color:#ffffff;
  }
  .line_left:hover::before{
    border-color:#009cff;
  }
  .line_right:hover::before{
    border-color:#009cff;
  }
</style>
