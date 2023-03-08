<template>
  <div class="footer_card">
    <div class="footer_inner">
      <div class="card_img">
        <img src="../assets/dd.png" alt="">
      </div>
      <div class="footer-sitemap">
        <p class="link_title">青少年编程</p>
        <div style="display: flex;">
          <div class="link_ti link_list">
            <ul>
              <li>首页</li>
              <li>实验室</li>
              <li>课程</li>
              <li>名师团</li>
              <li>校园</li>
              <li>社区</li>
            </ul>
          </div>
          <div class="link_ti link_list">
            <ul>
              <li>追梦营</li>
              <li>CodingDay</li>
            </ul>
          </div>
        </div>
      </div>
      <div>
        <p class="link_title">友情链接</p>
        <div class="link_ti link_list">
          <ul>
            <li>腾讯游戏追梦计划</li>
            <li>小鹅营地</li>
            <li>智启学堂</li>
            <li>腾讯工蜂</li>
          </ul>
        </div>
      </div>
      <div class="footer-qrcode">
        <div class="imgwrap">
          <img src="../assets/erwm.png" alt="">
        </div>
        <p class="qr_title">关注扣叮公众号<br />携手创造孩子未来</p>
      </div>
    </div>
    <div class="footer-ft">
      <p style="flex: 1;">Copyright © 1998 - 2023 Tencent. All Rights Reserved. 腾讯公司 版权所有</p>
      <p>
        <a href="#" style="color: #4a596f;">服务协议</a>
        <span class="line">|</span>
        <a href="#" style="color: #4a596f;">隐私政策</a>
        <span class="line">|</span>
        <a href="#" style="color: #4a596f;">版权保护投诉指引</a>
      </p>
    </div>
  </div>
</template>

<script>
</script>

<style lang="scss" scoped>
  .footer_card {
    width: 100%;
    background: #fff;
    padding: 35px 0;
    font-size: 14px;
  }

  .footer_inner {
    position: relative;
    display: flex;
    width: 1200px;
    margin: 0 auto;
  }

  .card_img {
    img {
      width: 180px;
    }
  }

  .footer-sitemap {
    margin: 0 40px 0 180px;
  }

  .link_title {
    font-size: 16px;
    color: rgba(74, 89, 111, 0.6);
    margin-bottom: 12px;
  }

  .link_ti ul {
    margin: 0;
    padding: 0;

    li {
      line-height: 28px;
    }
  }

  .link_list {
    min-width: 130px;
    margin-right: 40px;
  }

  .footer-qrcode {
    position: absolute;
    right: 0;
    top: 0;
  }

  .imgwrap {
    border: 1px solid #eff3f8;
    width: 120px;
    height: 120px;
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 4px;
    margin-bottom: 6px;
  }

  .qr_title {
    text-align: center;
    color: rgba(74, 89, 111, 0.6);
  }

  .footer-ft {
    width: 1200px;
    margin: 0 auto;
    display: flex;
    height: 60px;
    align-items: center;
    border-top: 1px solid #eff3f8;
    margin-top: 30px;
  }

  .line {
    color: rgba(74, 89, 111, 0.2);
    margin: 0 10px;
  }
</style>
