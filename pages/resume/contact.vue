<template>
  <div class="home-container">
    <h1 class="titleh1">
      关于我
    </h1>
    <aside class="question-aside width900">
      <div class="left-div">
        <section
          v-for="(item ,index) in menuList"
          :key="index"
          class="tab-section"
          :class="'tabSection'+index"
        >
          <p
            class="title-p"
            :class="[index == activeIndex && showQuestion[index].showIndex? 'isActive':'']"
            @click="titlepFn(index)"
          >
            {{ item.title }}
          </p>
          <ul
            class="menu-ul"
            :class="[index == activeIndex && showQuestion[index].showIndex ? 'isulActive':'defaultul']"
          >
            <li
              v-for="(item2 ,index2) in item.tabMenuList"
              :key="index2"
              class="menu-li"
              :class="{'onmenuli':index2 == activeMenuLI2 && index == activeMenuLI }"
              @click="menuliFn(index,index2)"
            >
              {{ item2 }}
            </li>
          </ul>
        </section>
      </div>
      <div class="right-div">
        <section v-show="0 == showRIndex" class="detail-section">
          <ul class="contact-ul">
            <li class="contact-li">
              电话：13121718971
            </li>
            <li class="contact-li">
              邮箱：1309264003@qq.com
            </li>
            <li class="contact-li">
              微信：lyc_8023
            </li>
            <li class="contact-li">
              QQ：1309264003
            </li>
          </ul>
        </section>
        <section v-show="1 == showRIndex">
          <ul class="contact-ul">
            <li class="edu-li">
              毕业院校：山东聊城大学
            </li>
            <li class="edu-li">
              专业：软件工程
            </li>
            <li class="edu-li">
              学历：本科
            </li>
          </ul>
        </section>
        <section v-show="2 == showRIndex">
          <ul class="myself-ul">
            <li
              class="myself-li"
            >
              带过前端团队，追求页面美观性能优化代码规范，能快速使用常见插件，开发效率高，逻辑思维强，对设计以及后台均有涉及，希望找一份稳定又富有挑战性的工作。
            </li>
            <li class="myself-li">
              我听力不是特别的好(介意的话别打电话来面试哦，麻烦啦)，但是这么多年来还是完全可以胜任一份前端工作的。要是有机会面试到自己的话，希望您可以多一份耐心来找我聊聊我们前端的知识。
            </li>
            <li class="myself-li">
              热爱技术，爱好很多，譬如打乒乓球，篮球，网球，羽毛球，爬山，摄影，跑步，轮滑等。
            </li>
          </ul>
        </section>
        <section v-show="3 == showRIndex">
          <p class="myselef-p">
            个人博客：<a href="http://coolyc.win/" class="a-link">http://coolyc.win/</a>
          </p>
          <p class="myselef-p">
            个人博客：<a href="https://segmentfault.com/u/lvtu/articles" class="a-link">https://segmentfault.com/u/lvtu/articles</a>
          </p>
        </section>
        <!-- <section v-show="4 == showRIndex">
          <p class="myselef-p">
            闲来无事记录的一些博客，附上地址：
            <a href="https://blog.csdn.net/u013018357" class="a-link">点我~</a>
          </p>
        </section> -->
      </div>
    </aside>
  </div>
</template>
<script>
const menuList = [
  {
    title: '基本信息',
    tabMenuList: ['联系方式', '教育经历', '自我评价']
  },
  {
    title: '博客技术',
    tabMenuList: ['博客']
  }
]
export default {
  data() {
    return {
      menuList: menuList,
      activeIndex: 0,
      showQuestion: [
        { showIndex: true },
        { showIndex: false },
        { showIndex: false }
      ],
      activeMenuLI: 0,
      activeMenuLI2: 0,
      showRIndex: 0
    }
  },
  methods: {
    titlepFn(index) {
      if (this.activeIndex !== index) {
        this.showQuestion[this.activeIndex].showIndex = false
      }
      this.activeIndex = index
      this.showQuestion[index].showIndex = !this.showQuestion[index].showIndex
    },
    menuliFn(index, index2) {
      this.activeMenuLI = index
      this.activeMenuLI2 = index2
      if (index === 0) {
        this.showRIndex = index2
      } else {
        let len = 0
        for (let i = 0; i < index; i++) {
          len += this.menuList[i].tabMenuList.length
        }
        len += index2
        this.showRIndex = len
      }
    }
  }
}
</script>
<style scoped lang="less">
@baseColor: #777;
.height40 {
  height: 40px;
  line-height: 40px;
}
.border {
  border: 1px solid #e8e8e8;
}
.bgSize {
  background-size: 18px;
}
.comlifp {
  font-size: 14px;
  padding-left: 30px;
}
.commyself {
  color: #666;
  line-height: 22px;
  word-break: break-all;
  font-size: 14px;
  margin-bottom: 10px;
}
.home-container {
  padding: 20px 0px 40px 0px;
  .question-aside {
    display: flex;
    margin-bottom: 100px;
    .border;
    margin-top: 20px;
    background: white;
    .left-div {
      padding: 15px 0px 0px 0px;
      width: 240px;
      border-right: 1px solid #e8e8e8;
      .title-p {
        .height40;
        color: #555;
        font-weight: bold;
        font-size: 16px;
        padding-left: 15px;
        position: relative;
        &:hover {
          color: @baseColor;
        }
        &::after {
          content: 'v';
          position: absolute;
          right: 15px;
          color: #999;
          font-weight: normal;
          transform: scaleY(0.6);
          transition: 0.3s;
        }
        &.isActive::after {
          transform: rotate(180deg) scaleY(0.6);
        }
      }
      .menu-ul {
        height: 0px;
        transform: scaleY(0);
        transform-origin: top center;
        transition: 0.3s linear;
        .menu-li {
          padding-left: 15px;
          .height40;
          color: #777;
          font-size: 14px;
          &:hover {
            background: #f5f5f5;
          }
        }
        .onmenuli {
          color: #222;
          background: #f5f5f5;
          border-right: 2px solid @baseColor;
        }
      }
      .isulActive {
        height: 120px;
        transform: scaleY(1) !important;
      }
    }
    .right-div {
      width: calc(100% - 240px);
      padding: 30px;
      .contact-ul {
        .edu-li {
          .height40;
          .comlifp;
          padding-left: 0px;
        }
        .contact-li {
          .comlifp;
          .height40;
          &:nth-child(1) {
            background: url('~@/assets/resume/tel.png') no-repeat left center;
            .bgSize;
          }
          &:nth-child(2) {
            background: url('~@/assets/resume/email.png') no-repeat left center;
            .bgSize;
          }
          &:nth-child(3) {
            background: url('~@/assets/resume/wx.png') no-repeat left center;
            .bgSize;
          }
          &:nth-child(4) {
            background: url('~@/assets/resume/qq.png') no-repeat left center;
            .bgSize;
          }
        }
      }
      .myselef-p {
        .commyself;
        .a-link {
          color: #222;
          font-weight: bolder;
          text-decoration: underline;
        }
      }
      .myself-ul {
        .myself-li {
          margin-left: 18px;
          list-style-type: disc;
          .commyself;
        }
      }
    }
  }
}
@media screen and (max-width: 640px) {
  .home-container {
    .question-aside {
      width: 100%;
      .left-div {
        width: 35%;
      }
      .right-div {
        width: calc(100% - 35%);
        padding: 15px;
      }
    }
  }
}
</style>
