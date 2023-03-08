<template>
  <div class="hello">
    <div class="head">
      <div class="head_left">
        <a class="head_gnyx center_in" href="http://zhuimeng.qq.com/" target="_blank">
          <img class="img_zm" src="../assets/zm.png" alt="">
        </a>
        <span class="line"></span>
        <a class="head_cogin center_in" href="http://shuimeng.qq.com/" target="_blank">
          <img class="img_dd" src="../assets/dd1.png" alt="">
        </a>
      </div>
      <div class="head_right" name="nav">
        <ul class="ec-header-menu">
          <li class="ec-header-menu-item " v-for="(item,index) in list" :key="index">
            <a href="#" class="ec-header-menu-item-link" :class="item.flag ? 'link_blue' :''" @click="change_bg(item)">{{item.name}}</a>
          </li>
        </ul>
        <div>
          <Dropdown title="赛事活动" :list="activityList" :num="true"></Dropdown>
        </div>
      </div>
      <div class="btn_right">
        <Dropdown title="立即创作" :list="creationList" :num="false"></Dropdown>
        <div class="title_cz">登录</div>
      </div>
    </div>
    <div>
      <SwiperCom style="width: 100%;" :gallery="gallery"></SwiperCom>
    </div>
    <div class="notice">叮叮头条</div>
    <div style="width: 100%;height: 376px;"></div>
    <div class="card_xx" id="content">
      <p class="title_h2">编程好工具，学习更轻松</p>
      <p class="title_sq">选择适合你的编程神器</p>
      <div id="card_tab">
        <div class="top">
          <div class="crad" :class="{ highLight: whichIndex == index }" v-for="(item, index) in cardArr" :key="index"
            @click=" whichIndex = index;componentId = item.componentId;" v-if="index < 7">
            <div class="card_img" :class="{ image: whichIndex == index }">
              <img src="../assets/zy.png" alt="">
            </div>
            <div class="bt_itam_title">
              <span class="bt_title1" :class="{ bt_blue: whichIndex == index }">{{ item.componentName }}</span>
              <span class="bt_title2" :class="{ bt_blue: whichIndex == index }">{{ item.componentName }}</span>
            </div>
          </div>
        </div>
        <div class="bottom">
          <keep-alive>
            <component :is="componentId"></component>
          </keep-alive>
        </div>
      </div>
    </div>
    <div id="content" style="width: 100%;height: 700px;background-color: pink;" class="center_in">学好课</div>
    <div id="content" style="width: 100%;height: 700px;background-color: darkgoldenrod;" class="center_in">好作品
    </div>
    <div id="content" style="width: 100%;height: 700px;background-color: red;" class="center_in">资讯</div>
    <div id="content" style="width: 100%;height: 700px;background-color: mediumvioletred;" class="center_in">校园
    </div>
    <div class="sidebar" :class="excessive ? 'reveal' : 'ensconce'">
      <div class="anchor">
        <!-- 导航区域 -->
        <ul class="navs">
          <li @click="scrollTo(0)" :class="{active: active===0}">
            <span class="iconfont icon-diannaozhengji" :class="{active: active===0}"></span>
            <p :class="{active: active===0}">实验室</p>
          </li>
          <li :class="{active: active===1}" @click="scrollTo(1)">
            <span class="iconfont icon-tushu" :class="{active: active===1}"></span>
            <p :class="{active: active===1}">学好课</p>
          </li>
          <li :class="{active: active===2}" @click="scrollTo(2)">
            <span class="iconfont icon-shoucang" :class="{active: active===2}"></span>
            <p :class="{active: active===2}">好作品</p>
          </li>
          <li :class="{active: active===3}" @click="scrollTo(3)">
            <span class="iconfont icon-tushu" :class="{active: active===3}"></span>
            <p :class="{active: active===3}">资讯</p>
          </li>
          <li :class="{active: active===4}" @click="scrollTo(4)">
            <span class="iconfont icon-xiaoyuan" :class="{active: active===4}"></span>
            <p :class="{active: active===4}">校园</p>
          </li>
          <li :class="{active: active===9}" @click="scrollTo(9)">
            <span class="iconfont icon-rocket" :class="{active: active===9}"></span>
            <p :class="{active: active===9}">回顶部</p>
          </li>
        </ul>
      </div>
      <div class="circle"></div>
      <div class="circle"></div>
    </div>
    <Footer></Footer>
  </div>
</template>

<script>
  import Dropdown from "@/components/dropdown";
  import SwiperCom from '@/components/SwiperCom.vue'
  import one from "@/components/one";
  import two from "@/components/two";
  import three from "@/components/three";
  import four from "@/components/four";
  import Footer from "@/components/footer";
  export default {
    components: {
      Dropdown,
      SwiperCom,
      one,
      two,
      three,
      four,
      Footer,
    },
    name: 'Home',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App',
        list: [{
            name: '首页',
            flag: false,
          },
          {
            name: '实验室',
            flag: false,
          },
          {
            name: '课程',
            flag: false,
          },
          {
            name: '名师团',
            flag: false,
          },
          {
            name: '校园',
            flag: false,
          },
          {
            name: '社区',
            flag: false,
          },
          {
            name: '追梦营',
            flag: false,
          },
          {
            name: 'CodingDay',
            flag: false,
          },
        ],
        activityList: [{
            name: '2023年NOC扣叮创意编程',
          },
          {
            name: '2023年第五届腾讯青少年人工智能追梦营',
          },
        ],
        creationList: [{
          name: '创意实验室',
        }, {
          name: 'Python实验室',
        }, {
          name: '3D实验室',
        }, {
          name: '人工智能实验室',
        }, {
          name: '游戏实验室',
        }, {
          name: '艺术(p5)实验室',
        }, {
          name: '硬件实验室',
        }, {
          name: 'JS实验室',
        }, ],
        gallery: [{
            img: "https://cdn.uviewui.com/uview/swiper/swiper1.png",
            title: '2023NOC扣叮创意编程'
          },
          {
            img: "https://cdn.uviewui.com/uview/swiper/swiper2.png",
            title: '2023NOC扣叮创意编2程'
          },
          {
            img: "https://cdn.uviewui.com/uview/swiper/swiper3.png",
            title: '2023NOC扣叮创意编1程'
          },
        ],
        whichIndex: 0,
        componentId: "one",
        cardArr: [{
            componentName: "动态组件一",
            componentId: "one",
          },
          {
            componentName: "动态组件二",
            componentId: "two",
          },
          {
            componentName: "动态组件三",
            componentId: "three",
          },
          {
            componentName: "动态组件四",
            componentId: "four",
          },
          {
            componentName: "动态组件四",
            componentId: "four",
          },
          {
            componentName: "动态组件四",
            componentId: "four",
          },
          {
            componentName: "动态组件四",
            componentId: "four",
          },
          {
            componentName: "动态组件四",
            componentId: "four",
          },
          {
            componentName: "动态组件四",
            componentId: "four",
          },
        ],
        active: 0, // 当前激活的导航索引
        excessive: true,
      }
    },
    mounted() {
      // 监听滚动事件
      window.addEventListener('scroll', this.onScroll, false)
    },
    destroy() {
      // 必须移除监听器，不然当该vue组件被销毁了，监听器还在就会出错
      window.removeEventListener('scroll', this.onScroll)
    },
    methods: {
      change_bg(obj) {
        console.log(obj)
        this.list.forEach(item=>{
          if(item.name == obj.name){
            item.flag = true
          }else{
            item.flag = false
          }
        })
      },
      // 滚动监听器
      onScroll() {
        // 获取所有锚点元素
        const navContents = document.querySelectorAll('#content')
        // 所有锚点元素的 offsetTop
        const offsetTopArr = []
        navContents.forEach(item => {
          offsetTopArr.push(item.offsetTop)
        })
        // 获取当前文档流的 scrollTop
        const scrollTop = document.documentElement.scrollTop || document.body.scrollTop
        // 定义当前点亮的导航下标
        let navIndex = 0
        for (let n = 0; n < offsetTopArr.length; n++) {
          // 如果 scrollTop 大于等于第n个元素的 offsetTop 则说明 n-1 的内容已经完全不可见
          // 那么此时导航索引就应该是n了
          if (scrollTop >= offsetTopArr[n]) {
            navIndex = n
          }
        }
        if (scrollTop > offsetTopArr[0] - 200) {
          this.excessive = false
        } else {
          this.excessive = true
        }
        this.active = navIndex
      },

      // 跳转到指定索引的元素
      scrollTo(index) {
        this.active = index
        if (index == 9) {
          document.documentElement.scrollTop = 0;
          return
        }
        const targetOffsetTop = document.querySelectorAll('#content')[index].offsetTop
        // 获取当前 offsetTop
        let scrollTop = document.documentElement.scrollTop || document.body.scrollTop
        // 定义一次跳 50 个像素，数字越大跳得越快，但是会有掉帧得感觉，步子迈大了会扯到蛋
        const STEP = 50
        // 判断是往下滑还是往上滑
        if (scrollTop > targetOffsetTop) {
          // 往上滑
          smoothUp()
        } else {
          // 往下滑
          smoothDown()
        }
        // 定义往下滑函数
        function smoothDown() {
          // alert('下滑')
          // 如果当前 scrollTop 小于 targetOffsetTop 说明视口还没滑到指定位置\
          if (scrollTop < targetOffsetTop) {
            // 如果和目标相差距离大于等于 STEP 就跳 STEP
            // 否则直接跳到目标点，目标是为了防止跳过了。
            if (targetOffsetTop - scrollTop >= STEP) {
              // alert('22')
              scrollTop += STEP
            } else {
              // alert('33')
              scrollTop = targetOffsetTop
            }
            document.body.scrollTop = scrollTop + 1
            document.documentElement.scrollTop = scrollTop + 1
            requestAnimationFrame(smoothDown)
          } else {
            console.log('else')
          }
        };
        // 定义往上滑函数
        function smoothUp() {
          if (scrollTop > targetOffsetTop) {
            if (scrollTop - targetOffsetTop >= STEP) {
              scrollTop -= STEP
            } else {
              scrollTop = targetOffsetTop
            }
            document.body.scrollTop = scrollTop + 1
            document.documentElement.scrollTop = scrollTop + 1
            requestAnimationFrame(smoothUp)
          }
        }
      }
    }
  }
</script>
<style lang="scss" scoped>
  .hello {
    color: #4a596f;
    background-color: #eff3f8;
  }

  .head {
    display: flex;
    background-color: #fff;
  }

  .head_left {
    padding-left: 40px;
    position: relative;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
  }

  .head_gnyx {
    img {
      width: 180px;
      height: 52px;
      background-size: 180px 52px;
    }
  }

  .line {
    height: 25px;
    width: 1px;
    background: #d4dce8;
    display: block;
    margin: 0 10px;
  }

  .head_cogin {
    img {
      width: 133px;
      height: 57px;
      background-size: 133px 57px;
    }
  }

  .head_right {
    display: flex;
    align-items: center;
  }

  .ec-header-menu {
    margin: 0px 0px 0px 20px;
    padding: 0px;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
  }

  .ec-header-menu-item {
    border-radius: 26px;
    transition: all 200ms;
    position: relative;
  }

  .ec-header-menu-item-link {
    color: #4a596f;
    padding: 0 28px;
    line-height: 42px;
    display: block;
  }

  .ec-header-menu-item-link:hover {
    background-color: #eff3f8;
    border-radius: 40px;
  }
  .link_blue{
    color: #0080ff;
    font-weight: bold;
  }
  .ec-header-menu-item:nth-child(9) .ec-header-menu-item-link::after {
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 6px 4px 0 4px;
    border-color: #0080ff transparent transparent transparent;
    display: inline-block;
    content: '';
    margin-left: 6px;
    transition: all 200ms;
    vertical-align: 2px;
  }

  .ec-header-menu-item:nth-child(9) .ec-header-menu-item-link:hover::after {
    transform: rotate(180deg);
  }

  .btn_right {
    position: absolute;
    right: 40px;
    top: 0;
    height: 60px;
    display: flex;
    flex-flow: row wrap;
    align-items: center;
  }

  .btn_cz {
    transition: all 0.5s ease;
    width: 112px;
    line-height: 34px;
    background-color: #0080ff;
    border-radius: 17px;
    color: #fff;
    text-align: center;
    font-size: 16px;
    cursor: pointer;
  }

  .btn_cz::after {
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 6px 4px 0 4px;
    border-color: #fff transparent transparent transparent;
    display: inline-block;
    content: '';
    margin-left: 6px;
    transition: all 200ms;
    vertical-align: 2px;
  }

  .btn_cz:hover::after {
    transform: rotate(180deg);
  }

  .btn_cz:hover {
    background-color: #009cff;
  }

  .title_cz {
    margin: 0 0 0 20px;
    line-height: 60px;
    color: #4a596f;
  }

  .notice {
    display: flex;
    align-items: center;
    height: 70px;
    width: 1144px;
    margin: 0 auto;
    background: #fff;
    border-radius: 0 0 12px 12px;
    padding: 0 28px;
    font-weight: bold;
    color: #009cff;
  }


  .card_xx {
    display: flex;
    flex-wrap: wrap;
    flex-direction: column;
    align-items: center;
  }

  .title_h2 {
    margin: 0;
    font-size: 40px;
    font-weight: bold;
  }

  .title_sq {
    font-size: 16px;
    color: rgba(74, 89, 111, 0.6);
    margin-bottom: 26px;
  }




  #card_tab {
    width: 1200px;
    height: 600px;
    background-color: #ffffff;
    border-radius: 12px;
    box-sizing: border-box;
    margin-bottom: 70px;
    display: flex;
    overflow: hidden;

    .top {
      width: 290px;
      display: flex;
      flex-direction: column;
      background-color: #009cff;

      .crad {
        width: calc(100% - 40px);
        height: 82px;
        line-height: 82px;
        text-align: center;
        display: flex;
        align-items: center;
        // justify-content: center;
        padding: 0 20px;
        border-bottom: 1px solid #0090ff;
        transition: all 200ms;
      }

      .highLight {
        height: 82px;
        position: relative;
        background-color: #fff;
      }

      .highLight::before {
        content: " ";
        display: inline-block;
        position: absolute;
        width: 4px;
        height: 100%;
        left: 0;
        background-color: #0080ff;
      }
    }

    .bottom {
      width: 810px;
      margin-left: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }

  .crad:hover .card_img {
    background-color: rgb(246, 202, 219);
    border-radius: 50%;
    transition: all 200ms;

    img {
      transition: all 200ms;
      width: 22px;
    }
  }

  .card_img {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 48px;
    height: 48px;
    background-color: #ffffff;
    border-radius: 12px;
    margin-right: 14px;

    img {
      width: 25px;
    }
  }

  .image {
    background-color: rgb(246, 202, 219);
    border-radius: 50%;
  }

  .bt_itam_title {
    display: flex;
    flex-direction: column;
    align-items: flex-start;

    .bt_title1 {
      color: #fff;
      font-size: 18px;
    }

    .bt_title2 {
      color: #fff;
      font-size: 12px;
    }

    .bt_blue {
      color: #498ff6;
    }

    span {
      line-height: 22px;
      overflow: hidden;
      text-overflow: ellipsis;
      white-space: nowrap;
      font-size: 18px;
    }
  }

  .sidebar {
    position: fixed;
    width: 90px !important;
    right: 20px;
    bottom: 14px;
    z-index: 2002;
    display: flex;
    flex-direction: column;
    width: fit-content;
    width: -webkit-fit-content;
    width: -moz-fit-content;
    overflow: hidden;
    max-height: 0px;
    transition: max-height 0.3s;
  }

  .reveal {
    max-height: 0px;
    transition: max-height 0.3s;
  }

  .ensconce {
    transition: max-height 0.3s;
    max-height: 600px !important;
    z-index: 2003;
  }

  .anchor {
    width: 60px;
    margin: 10px auto;
    background: #fff;
    border-radius: 8px;
    overflow: hidden;
    // box-shadow: 0px 0px 4px rgb(74 89 111 / 20%);
    filter: drop-shadow(0 0 6px rgba(192, 192, 192, .4));
    transition: all 200ms;

    .navs {
      width: 100%;
      margin: 0;
      padding: 0;
      text-align: center;

      li {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        height: 68px;
        font-size: 12px;
        border-bottom: 1px solid #eff3f8;

        span {
          font-size: 18px;
          color: rgba(74, 89, 111, 0.6);
        }

        p {
          margin-top: 6px;
          color: rgba(74, 89, 111, 0.6);
        }
      }
    }
  }

  /* 当导航被点亮后改变颜色 */
  .navs .active {
    color: #009cff !important;
    background-color: #fff !important;
  }

  .navs li:hover {
    cursor: pointer;
    background-color: #009cff;

    span {
      color: #fff;
    }

    p {
      color: #fff;
    }
  }

  .circle {
    width: 60px;
    height: 60px;
    background: #fff;
    border-radius: 100%;
    position: relative;
    margin: 0 auto 10px;
    filter: drop-shadow(0 0 6px rgba(192, 192, 192, .4));
  }
  .current{
  color:#ffffff;
  background:blue;
  }
</style>
