<template>
  <div class="hello">
    <div class="head">
      <div class="head_left">
        <a class="head_gnyx center_in" href="http://zhuimeng.qq.com/" target="_blank">
          <img class="img_zm" src="../assets/zm.png" alt="">
        </a>
        <span class="line"></span>
        <a class="head_cogin center_in" href="http://shuimeng.qq.com/" target="_blank">
          <img class="img_dd" src="../assets/dd.png" alt="">
        </a>
      </div>
      <div class="head_right">
        <ul class="ec-header-menu">
          <li class="ec-header-menu-item " v-for="(item,index) in list" :key="index">
            <a href="#" class="ec-header-menu-item-link">{{item.name}}</a>
          </li>
        </ul>
      </div>
      <div class="btn_right">
        <div class="btn_cz">立即创作</div>
        <div class="title_cz">登录</div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'Home',
    data() {
      return {
        msg: 'Welcome to Your Vue.js App',
        list: [{
            name: '首页',
          },
          {
            name: '实验室',
          },
          {
            name: '课程',
          },
          {
            name: '名师团',
          },
          {
            name: '校园',
          },
          {
            name: '社区',
          },
          {
            name: '追梦营',
          },
          {
            name: 'CodingDay',
          },
          {
            name: '赛事活动',
            children: [{
                name: '2023年NOC扣叮创意编程',
              },
              {
                name: '2023年第五届腾讯青少年人工智能追梦营',
              },
            ]
          },
        ]
      }
    }
  }
</script>

<style lang="scss" scoped>
  .head {
    display: flex;
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
  .btn_cz:hover{
    background-color: #009cff;
  }
  .title_cz {
    margin: 0 0 0 20px;
    line-height: 60px;
    color: #4a596f;
  }
</style>
