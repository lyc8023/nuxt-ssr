<template>
  <div class="resume-container">
    <h1 class="titleh1">
      前端经验
    </h1>
    <aside class="resume-aside width900">
      <section v-for="(item ,index) in resumeList" :key="index" class="resume-section">
        <p class="title-p">
          {{ item.title }}
        </p>
        <article class="tip-article">
          <ul class="tip-ul">
            <li v-for="(item3,index3) in item.tips" :key="index3" class="tip-li">
              {{ item3 }}
            </li>
          </ul>
        </article>
        <aside class="circle-aside">
          <div v-for="(item2, index2) in item.detailText" :key="index2" class="detail-div">
            <p class="detail-p">
              {{ item2.menuText }}
            </p>
            <p class="detail-textp">
              {{ item2.taskText }}
            </p>
          </div>
          <!--detail-div-->
        </aside>
      </section>
    </aside>
  </div>
</template>
<script>
import { resumeList } from './mixins/resume'
export default {
  data() {
    return {
      resumeList: resumeList
    }
  }
}
</script>
<style lang="less" scoped>
.resume-container {
  .resume-aside {
    margin-top: 20px;
    padding-bottom: 100px;
  }
  .resume-section {
    margin-bottom: 50px;
    .title-p {
      color: #555;
      font-size: 16px;
      font-weight: bold;
    }
    .tip-article {
      font-size: 12px;
      color: #999;
      margin-bottom: 15px;
      .tip-li {
        margin-top: 6px;
      }
    }
    .detail-p {
      color: #555;
      font-size: 14px;
      margin: 10px 0px;
    }
    .detail-textp {
      color: #777;
      font-size: 12px;
      word-break: break-all;
      line-height: 22px;
    }
    .circle-aside {
      position: relative;
      .detail-div {
        position: relative;
        padding-left: 40px;
        &::before {
          content: '';
          width: 12px;
          height: 12px;
          border-radius: 50%;
          background: #555;
          position: absolute;
          top: 4px;
          left: 0px;
          opacity: 0.5;
          transition: all 0.2s ease-in-out;
        }
        &:hover::before {
          background: black;
          transform: scale(1.2);
          opacity: 1;
        }
        &:hover {
          .detail-p {
            color: #555;
          }
        }
      }
    }
    .circle-aside::before {
      position: absolute;
      top: 0px;
      content: '';
      top: 16px;
      left: 6px;
      margin-left: -2px;
      height: 100%;
      width: 4px;
      background: #f5f5f5;
    }
  }
}
@media screen and (max-width: 640px) {
  .resume-aside {
    padding: 0px 4% 100px 4%;
    width: 100%;
    .detail-div {
      padding-left: 6%;
    }
  }
}
</style>
