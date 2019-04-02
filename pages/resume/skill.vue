<template>
  <div class="skill-container">
    <h1 class="titleh1">
      前端技术
    </h1>
    <p class="skill-p">
      skill-技能小清单~
    </p>
    <ul class="skill-ul">
      <li class="skill-li ex-li">
        koa
      </li>
      <li class="skill-li">
        jQuery
      </li>
    </ul>
    <ul class="skill-ul">
      <li class="skill-li small-li">
        es6
      </li>
      <li class="skill-li main-li">
        vue
      </li>
      <li class="skill-li">
        css3
      </li>
      <li class="skill-li small-li">
        canvas
      </li>
    </ul>
    <ul class="skill-ul">
      <li class="skill-li wx-li">
        小程序
      </li>
      <li class="skill-li">
        webpack
      </li>
      <li class="skill-li">
        gulp
      </li>
    </ul>
    <section class="skill-section">
      <p class="status-p">
        带过前端团队，追求页面美观性能优化代码规范，能快速使用常见插件，开发效率高，逻辑思维强，对设计以及后台均有涉及。
      </p>
      <p class="status-p">
        最近在学习node项目规范，研究前端调用GraphQL接口问题。
      </p>
    </section>
  </div>
</template>
<script>
export default {
  data() {
    return {}
  }
}
</script>
<style lang="less" scoped>
.skill-container {
  padding-bottom: 100px;
  .link-a {
    display: block;
    font-size: 20px;
    border-bottom: 1px solid green;
  }
  .link-a:nth-child(2) {
    font-size: 40px;
  }
  .skill-p {
    text-align: center;
    color: #555;
    font-size: 14px;
    margin: 20px;
  }
  .skill-ul {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    margin-bottom: 70px;
    .skill-li {
      padding-bottom: 2px;
      margin-right: 55px;
      border-bottom: 1px solid #999;
      color: #666;
      font-size: 20px;
      transition: all 0.3s ease-in-out;
      &:hover {
        transform: scale(1.2);
        border-bottom: 1px solid #222;
      }
    }
    .ex-li {
      font-size: 30px;
    }
    .main-li {
      font-size: 55px;
    }
    .small-li {
      font-size: 35px;
    }
    .wx-li {
      font-size: 30px;
    }
  }
  .skill-section {
    position: relative;
    margin: 0 auto;
    width: 600px;
    padding-left: 14px;
    .status-p {
      color: #555;
      font-size: 14px;
      word-break: break-all;
    }
    &::before {
      position: absolute;
      content: '';
      left: 0px;
      top: 0px;
      height: 100%;
      width: 4px;
      background: #f5f5f5;
    }
  }
}
@media screen and (max-width: 640px) {
  .skill-container {
    .skill-section {
      width: 100%;
      padding: 0% 7%;
      &::before {
        left: 4%;
      }
    }
    .skill-ul {
      flex-wrap: wrap;
      justify-content: space-around;
      .skill-li {
        margin-right: 0px;
      }
    }
  }
}
</style>
