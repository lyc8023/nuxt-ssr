<template>
  <div class="home">
    <p class="blackline" />
    <header>
      <section class="tx-section">
        <div class="tx-div">
          <img src="@/assets/resume/tx.jpg" alt class="tx-img">
        </div>
        <div class="name-div">
          <p class="name-p">
            李元成~
          </p>
          <p class="type-p">
            web前端工程师
          </p>
        </div>
      </section>
      <p class="sign-p">
        前端路上~填坑补坑创建路……
      </p>
      <!-- <img :src="`${publicPath}tx.jpg`" alt=""> -->
      <ul class="nav-ul">
        <li v-for="(item , index) in navList" :key="index" class="nav-li">
          <a class="a-nav" href="javascript:;" @click="currentTabComponent = item.name">
            <img :src="item.imgUrl" alt class="skill-img">
            <p class="nav-p">
              {{ item.text }}
            </p>
          </a>
        </li>
      </ul>
    </header>
    <div class="tabComponent pd40">
      <transition name="fade" mode="out-in" appear>
        <component :is="currentTabComponent" />
      </transition>
    </div>
    <a href="/ssr/doc/lyc.docx" download="李元成的简历.docx" target="blank" class="download-p">
      <img src="@/assets/resume/download.png" alt="" class="load-img">
    </a>
  </div>
</template>

<script>
import contact from './contact.vue'
import resume from './resume.vue'
import skill from './skill.vue'
export default {
  name: 'Home',
  components: {
    skill,
    resume,
    contact
  },
  data() {
    return {
      publicPath: process.env.BASE_URL,
      // jianli: require('/static/doc/lyc.docx'),
      currentTabComponent: 'resume',
      navList: [
        {
          name: 'resume',
          text: '前端经验',
          imgUrl: require('@/assets/resume/resume.png')
        },
        {
          name: 'skill',
          text: '前端技术',
          imgUrl: require('@/assets/resume/resume3.png')
        },
        {
          name: 'contact',
          text: '关于我',
          imgUrl: require('@/assets/resume/resume2.png')
        }
      ]
    }
  }
}
</script>
<style lang="less" >
* {
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
}
body,
html {
  height: 100%;
}
a {
  text-decoration: none;
}
li {
  list-style: none;
}
.pd40 {
  padding: 0 40px;
}
.titleh1 {
  color: #555;
  font-weight: bold;
  font-size: 22px;
  text-align: center;
  margin-top: 100px;
}
.width900 {
  max-width: 900px;
  margin: 0 auto;
}
.download-p {
  position: fixed;
  bottom: 100px;
  right: 100px;
  &::after {
    content: '下载简历';
    color: #888;
    font-size: 12px;
    position: absolute;
    bottom: 0px;
    left: 30px;
  }
  .load-img {
    width: 20px;
    height: 20px;
    cursor: pointer;
  }
}
@media screen and (max-width: 640px) {
  .titleh1 {
    margin-top: 70px;
  }
  .pd40 {
    padding: 0;
  }
  .download-p {
    bottom: 0px;
    text-align: center;
    right: 0px;
    width: 100%;
    height: 40px;
    line-height: 40px;
    background: #f5f5f5;
    z-index: 99;
    &::after {
      position: static;
      font-size: 16px;
    }
    .load-img {
      vertical-align: middle;
    }
  }
}

@baseColor: #555;
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.wh120 {
  width: 120px;
  height: 120px;
}
@rotateDeg: rotate3d(0, 1, 0, -180deg);
@rotateOrigin: 0% 50%;
.home {
  .blackline {
    width: 100%;
    height: 3px;
    background: black;
  }
  .tx-section {
    text-align: center;
    position: relative;
    .wh120;
    margin: 95px auto 0px;
    &:hover {
      transition: 0.5s;
      .tx-div {
        -webkit-transform: @rotateDeg;
        -moz-transform: @rotateDeg;
        -ms-transform: @rotateDeg;
        -o-transform: @rotateDeg;
        transform: @rotateDeg;
      }
    }
    .tx-div {
      -webkit-transform-origin: @rotateOrigin;
      -moz-transform-origin: @rotateOrigin;
      -ms-transform-origin: @rotateOrigin;
      -o-transform-origin: @rotateOrigin;
      transform-origin: @rotateOrigin;
      position: relative;
      margin: 0 auto;
      transition: all 0.5s ease-in-out;
      border-radius: 50%;
      .wh120;
      border: 1px solid rgba(0, 0, 0, 0.3);
      .tx-img {
        width: 100%;
        height: 100%;
        border-radius: 100%;
      }
      &::before {
        position: absolute;
        display: block;
        content: '';
        width: 100%;
        height: 100%;
        border-radius: 50%;
        -webkit-transition: all 0.35s ease-in-out;
        -moz-transition: all 0.35s ease-in-out;
        transition: all 0.35s ease-in-out;
      }
    }
    .name-div {
      position: absolute;
      .wh120;
      left: 50%;
      top: 0px;
      margin-left: -60px;
      background: black;
      opacity: 0.6;
      transform: scale(0.99);
      z-index: -1;
      border-radius: 50%;
      padding-top: 35px;
      color: white;
      text-align: center;
      .name-p {
        font-size: 16px;
        margin-bottom: 5px;
      }
      .type-p {
        font-size: 12px;
      }
    }
  }
  .sign-p {
    text-align: center;
    color: #999;
    margin-top: 15px;
  }
  .nav-ul {
    margin-top: 40px;
    display: flex;
    justify-content: center;
    .nav-li {
      margin-right: 60px;
      font-size: 14px;
      text-align: center;
      position: relative;
      .a-nav {
        color: #555;
        .skill-img {
          width: 12px;
          height: 12px;
        }
      }
      &::after {
        position: absolute;
        bottom: 0px;
        left: 0px;
        width: 100%;
        height: 1px;
        background: #222;
        content: '';
        transform: scaleX(0);
        visibility: hidden;
        transition: 0.2s ease-in-out;
      }
      &:hover::after {
        visibility: visible;
        transform: scaleX(1);
      }
      &:last-child {
        margin-right: 0px;
      }
    }
  }
}
</style>
