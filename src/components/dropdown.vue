<template>
  <div>
    <div class="drow">
      <a href="#" class="title" :class="num ? 'title1' :'title2'" @mouseover="state = true"
        @mouseleave="state = false">{{title}}</a>
      <div class="note" :style="{height:scrollH + 'px'}" :class="state? 'show' : 'conceal'">
        <!-- :class="state? 'show' : 'conceal'" -->
        <div class="item_title" v-for="(item,index) in list" :key="index" @mouseover="state = true"
          @mouseleave="state = false">
          <img src="../assets/zy.png" alt="" v-if="list.length > 2">
          <a href="#">{{item.name}}</a>
        </div>
        <span class="triangle"></span>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      num: {
        type: Boolean,
        default: () => {
          return true
        }
      },
      list: {
        type: Array,
        default: () => {
          return []
        }
      },
      title: {
        type: String,
        default: () => {
          return ''
        }
      },
    },
    data() {
      return {
        state: false,
        scrollH: '',
      }
    },
    created() {
      let scrollH = this.list.length * 40
      if (this.list.length <= 2) {
        scrollH = scrollH + 34
      }
      this.scrollH = scrollH
    },
    methods: {}
  }
</script>

<style lang="scss">

  .drow {
    position: relative;
    z-index: 999;
  }

  .note {
    position: absolute;
    width: 178px;
    height: 100px;
    background: #ffffff;
    border-radius: 5px;
    overflow: hidden;
    /*box-shadow: 0 0 10px 0px #000;*/
    filter: drop-shadow(0 0 6px rgba(192, 192, 192, .4));
  }

  .item_title {
    display: flex;
    align-items: center;
    padding: 10px 20px;

    img {
      width: 16px;
      height: 20px;
      margin-right: 10px;
    }

    a {
      font-size: 14px;
      color: #4a596f !important;
      display: block;
      display: flex;
      flex-flow: row wrap;
      align-items: center;
    }
  }

  .item_title:hover {
    background-color: #eff3f8;

    a {
      color: #0080ff !important;
    }
  }

  .triangle {
    border-left: 10px solid transparent;
    border-right: 10px solid transparent;
    border-bottom: 10px solid #ffffff;
    position: absolute;
    top: -10px;
    left: 50%;
    margin-left: -10px;
  }

  .show {
    display: block;
  }

  .conceal {
    display: none;
  }

  .title {
    padding: 0 28px;
    line-height: 42px;
    display: block;
  }

  .title2 {
    color: #ffffff !important;
    background-color: #0080ff;
    border-radius: 40px;
  }

  .title:hover::after {
    transform: rotate(180deg);
  }

  a:link,
  a:visited {
    color: #0080ff;
  }

  .title1::after {
    color: #0080ff !important;
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

  .title2::after {
    color: #ffffff !important;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 6px 4px 0 4px;
    border-color: #ffffff transparent transparent transparent;
    display: inline-block;
    content: '';
    margin-left: 6px;
    transition: all 200ms;
    vertical-align: 2px;
  }
</style>
