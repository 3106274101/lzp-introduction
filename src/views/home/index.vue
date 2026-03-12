<template>
  <section class="home-container" id="home">
    <Intro @mose="scrollToSection1"/>
    <section class="main-warp" id="about">
      <section class="banner">
               <img class="banner-cover"
                    alt="banner" src="../../assets/img/banner.jpg">
        <div class="banner-content">
          <div class="banner-container">
            <div class="row">
              <div class="row-col-left"></div>
              <div class="row-col-right">
                <div class="banner-text"
                     :style="`transform: translateX(-${state.titleAnimation?0:50}%)`">
                  <p class="text-tip">Hi! I'm {{ setting.websiteInfo.name || 'Li ZhiPeng' }}</p>
                  <p class="text-main">
                    {{ setting.websiteInfo.motto || "Welcome To My Personal Homepage! Let's Go!" }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
      <section class="main-container">
        <div class="container-row">
          <div class="container-left">
            <div class="sidebar" :style="`transform: translateY(-${state.titleAnimation?40:0}%)`">
              <div class="sidebar-card">
                <div class="sidebar-avatar">
                  <img class="avatar-img lazy-image "
                       :data-src="`https://img0.baidu.com/it/u=3240131412,3050737635&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500`">
                </div>
                <div class="sidebar-name">{{ setting.websiteInfo.occupation }}</div>
                <div class="sidebar-label">{{ setting.websiteInfo.occupationEn }}</div>
                <div class="c-divider c-mb-40"></div>
                <div class="sidebar-social">
                  邮箱：lzp_991125@163.com
                  <!-- <a :href="setting.userInfo.github" target="_blank"><i class="iconfont icon-github"></i></a> -->
                  <!-- <a :href="setting.userInfo.gitee" target="_blank"><i class="iconfont icon-gitee"></i></a> -->
                  <!--                  <a href="https://github.com/ZHYI-source" target="_blank"><i class="iconfont icon-github"></i></a>-->
                  <!--                  <a href="https://github.com/ZHYI-source" target="_blank"><i class="iconfont icon-github"></i></a>-->
                </div>
                <div class="c-divider c-mb-40 c-mt-40"></div>
                <ul class="sidebar-other">
                  <li class="other-item">
                    <span class="item-label">城市：</span>
                    <span class="item-label-light">{{ setting.userInfo.city || '-' }}</span>
                  </li>
                  <li class="other-item">
                    <span class="item-label">年龄：</span>
                    <span class="item-label-light">{{ setting.userInfo.age }}</span>
                  </li>

                  <li class="other-item">
                    <span class="item-label">微信：</span>
                  </li>
                  <div class="social">
                    <img width="120"
                         class="lazy-image"
                         :data-src="setting.userInfo.wx">
                    <!-- <img width="80"
                         class="lazy-image"
                         :data-src="setting.userInfo.qq"> -->
                  </div>
                </ul>
                <div class="c-divider c-mb-40"></div>

                <div class="sidebar-btn" @click="downloadResume">
                  <span>下载简历</span>
                  <!--                  <i class="iconfont icon-github"></i>-->
                </div>
                <span class="downResume" v-if="setting.userInfo.showResumeUrl" @click="downloadResume">下载简历</span>
              </div>
            </div>
          </div>
          <div class="container-right">
            <div class="container-right-content">
              <div class="brand-card-list">
                <div class="brand-card-item">
                  <div class="card-item">
                    <h3 class="card-item-title">5年</h3>
                    <div class="c-divider"></div>
                    <div class="card-item-content">工作年限</div>
                  </div>
                </div>
                <div class="brand-card-item">
                  <div class="card-item">
                    <h3 class="card-item-title">20 +</h3>
                    <div class="c-divider"></div>
                    <div class="card-item-content">实战经验</div>
                  </div>
                </div>
                <div class="brand-card-item">
                  <div class="card-item">
                    <h3 class="card-item-title">面议</h3>
                    <div class="c-divider"></div>
                    <div class="card-item-content">期望薪资</div>
                  </div>
                </div>
              </div>
              <section class="notice ">
                <div class="notice-line">
                  <span class="notice-title">📢 NOTICE：</span>
                  <div class="notice-desc">
                    {{ setting.websiteInfo.notice || '-' }}
                  </div>
                </div>
              </section>
              <section class="brand-tips">
                <ZySectionHeader title="Tips" titleNum="01"/>
                <blockquote class="my-story">
                  无趣的人想过着有趣的生活。
                  <br/>
                  每一步都是奇迹，每一天都是新的起点。
                  <img class="wx-logo lazy-image" width="120"
                       :data-src="setting.websiteInfo.wxMini">
                </blockquote>
              </section>

            </div>
          </div>
        </div>
        <section class="notice notice-temp c-mb-40">
          <div class="notice-line">
            <span class="notice-title">公告：</span>
            <div class="notice-desc">{{ setting.websiteInfo.notice || '-' }}
            </div>
          </div>
        </section>

        <section class="about">
          <ZySectionHeader title="自我介绍" titleNum="02"/>
          <!-- <section class="animate-me">
            "<span class="me-text me-text-a">三年前</span>，我踏上了<span class="me-text me-text-b">前端开发</span>的旅程
            ，从那时起，对前端技术<span class="me-text me-text-c">充满热情</span>，
            并迫不及待地构建各种<span class="me-text me-text-d">响应式</span>设计和<span class="me-text me-text-c">移动端</span>的开发。我比较注重
            <span class="me-text me-text-e">用户体验</span>、界面设计和<span class="me-text me-text-a">代码质量</span>，并具有<span
              class="me-text me-text-c">优化性能</span>和解决兼容性问题的经验。
            热衷于<span class="me-text me-text-c">创新</span>思维，喜欢思考和
            <span class="me-text me-text-c">解决问题</span>。追求自己的兴趣和激情，让每一天都充满<span class="me-text me-text-c">活力</span>和乐趣
          </section> -->

          <section class="animate-me">

            <div> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
              <span class="me-text me-text-a">五年</span>专业<span class="me-text me-text-b">前端开发</span>经验
            ，深耕<span class="me-text me-text-c">Vue3、React、UniApp</span>核心技术栈。精通<span class="me-text me-text-d">微前端、跨平台开发、数据可视化、3D场景渲染</span>等关键技术。具备<span class="me-text me-text-d">大型项目</span>从0到1<span class="me-text me-text-c">架构搭建与落地</span>的全流程经验。 </div>

            <div>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
              具备扎实的<span class="me-text me-text-d">技术基础</span>与精准的
            <span class="me-text me-text-e">技术选型</span>能力,根据项目需求制定最优<span class="me-text me-text-b">技术方案</span>，推动<span class="me-text me-text-a">前沿技术</span>在项目中落地，高效解决<span
              class="me-text me-text-c">多端适配、性能优化、系统集成</span>等核心技术问题。
            </div>

            <div>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
              拥有<span class="me-text me-text-c">商业</span>、高速交通、医疗等<span class="me-text me-text-c">多行业开发经验</span>能够快速理解不同行业
            <span class="me-text me-text-c">业务需求</span>实现技术与业务的<span class="me-text me-text-c">深度结合</span>，保障项目交付<span class="me-text me-text-e">质量与效率</span>！
            </div>

            
          </section>
        </section>
        <section class="resume c-mt-40 " id="resume">
          <ZySectionHeader title="工作经历" titleNum="03"/>
          <div class="resume-box skill-box">
            <div class="box-title">
              <span class="title-icon iconfont icon-Elephone_repair"> </span>
              <span class="text">技能</span>
            </div>
            <div class="box-item">
              <ul>
                <li><i class="icon iconfont icon-icon"></i>HTML</li>
                <li><i class="icon iconfont icon-icon"></i>CSS/SCSS/Less</li>
                <li><i class="icon iconfont icon-icon"></i>TailwindCSS</li>
                <li><i class="icon iconfont icon-icon"></i>JavaScript</li>
                <li><i class="icon iconfont icon-icon"></i>TypeScript</li>
              </ul>
            </div>
            <div class="box-item">
              <ul>
                <li><i class="icon iconfont icon-icon"></i>Vue.js</li>
                <li><i class="icon iconfont icon-icon"></i>React.js</li>
                <li><i class="icon iconfont icon-icon"></i>Canvas</li>
                <li><i class="icon iconfont icon-icon"></i>WebGL</li>
                <li><i class="icon iconfont icon-icon"></i>Thress.js</li>
              </ul>
            </div>
            <div class="box-item">
              <ul>
                <li><i class="icon iconfont icon-icon"></i>UniApp</li>
                <li><i class="icon iconfont icon-icon"></i>Webpack/Vite</li>
                <li><i class="icon iconfont icon-icon"></i>MicroApp</li>
                <li><i class="icon iconfont icon-icon"></i>Node.js</li>
                <li><i class="icon iconfont icon-icon"></i>Mysql/MongoDB</li>
              </ul>
            </div>
            <div class="box-item">
              <ul>
                <li><i class="icon iconfont icon-icon"></i>响应式开发</li>
                <li><i class="icon iconfont icon-icon"></i>大屏可视化</li>
                <li><i class="icon iconfont icon-icon"></i>多端跨平台</li>
                <li><i class="icon iconfont icon-icon"></i>全流程项目管理</li>
                <li><i class="icon iconfont icon-icon"></i>AI系统集成</li>
              </ul>
            </div>
          </div>
          <div class="resume-box icon-animation" style="border: 1px solid #eee">
            <div class="box-title">
              <span class="title-icon iconfont icon-a-xingshizhexueshekebaogaohuishenpibiao"> </span>
              <span class="text">经历</span>
            </div>
            <ExperienceStep/>
          </div>
          <!-- <div class="resume-box best-box">
            <div class="box-title">
              <span class="title-icon iconfont icon-zhuomian-diannaoxianshiqi"> </span>
              <span class="text">兴趣爱好</span>
            </div>
            <div class="box-item">
              <i class="icon icon-b iconfont icon-a-developer_outlineI"></i>
              <div class="best-text">热爱编程工作。每一行代码都是我对未知世界的探索.每一次bug的战胜，都是一次成长的飞跃.</div>
            </div>
            <div class="box-item">
              <i class="icon icon-e iconfont icon-yingxionglianmeng"></i>
              <div class="best-text">享受在LOL中和好友默契十足的配合，无论输赢，都是锻炼意志的历练.</div>
            </div>
            <div class="box-item">
              <i class="icon icon-d iconfont icon-lvyoufabu"></i>
              <div class="best-text">旅游是我心中永不停歇的冒险！我喜欢追逐风景，感受异域文化的魅力.</div>
            </div>
          </div> -->
        </section>
        <section class="works c-mt-40 c-mb-40" id="work">
          <ZySectionHeader title="作品集" titleNum="04"/>
          <div class="work-box">
            <!--        <ul class="work-menu">
                          <li>ALL</li>
                          <li>VUE</li>
                          <li>REACT</li>
                          <li>移动H5</li>
                          <li>小程序</li>
                        </ul>-->
            <div class="work-list">
              <div class="work-item" :title="item.abstract" v-for="item in state.portfoliosData"
                   @click="viewWorks(item)">
                <img class="work-cover lazy-image" v-bind:data-src="item.cover"
                     alt="Lazy Loaded Image">
                <div class="work-info">
                  <div class="work-info-icon"><i class="iconfont icon-chakan2"></i></div>
                  <div class="work-info-title">{{ item.title }}</div>
                  <!--                  <div class="work-info-desc"> {{ item.abstract }}</div>-->
                </div>
              </div>
              <!-- <div class="work-item" @click="goToPage('/Portfolio')">
                <img class="work-cover lazy-image"
                     v-bind:data-src="`http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545299360.png`">
                <div class="work-info work-more">
                  <div class="work-info-icon"><i class="iconfont icon-click"></i></div>
                  <div class="work-info-title">MORE</div>
                </div>
              </div> -->
            </div>
          </div>
        </section>
        <!--        <section class="blog c-mt-40" id="blog">
                  <ZySectionHeader title="BLOG" titleNum="05"/>
                  <ul class="blog-menu">
                    <li>ALL</li>
                    <li>VUE</li>
                    <li>REACT</li>
                    <li>移动H5</li>
                    <li>小程序</li>
                  </ul>
                  <div class="blog-box">
                    <div class="blog-left">
                      <div class="new-block">
                        <div class="inner-box">
                          <div class="image">
                            <img class="lazy-image" v-bind:data-src="`https://picsum.photos/id/400/400/`"
                                 alt="Lazy Loaded Image">
                          </div>
                          <div class="over-box">
                            <div class="hvr-lower">
                              <div class="title">
                                想做一只小青蛙🐸，开心时，跳水，不开心时，也跳水。
                              </div>
                              <div class="info">
                                <div class="i-blk"><span class="icon far fa-comment"></span> 5 comments
                                </div>
                                <div class="i-blk"><span class="icon far fa-user"></span> admin</div>
                              </div>
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="news-block-two" v-for="item in 4" @click="goToPage('PostDetail',{id:item})">
                        <div class="inner-box">
                          <div class="image">
                            <img class="lazy-image" v-bind:data-src="`https://picsum.photos/id/${item + 32}/600/400/`"
                                 alt="cover">
                          </div>
                          <div class="text-box">
                            <div class="title">
                              踏遍千山万水，行走在世界的怀抱。旅游是我心中永不停歇的冒险！我喜欢追逐风景，感受异域文化的魅力.
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                    <div class="blog-right blog-left">
                      <div class="news-block-two" v-for="item in 4" @click="goToPage('PostDetail',{id:item})">
                        <div class="inner-box">
                          <div class="image">
                            <img class="lazy-image" v-bind:data-src="`https://picsum.photos/id/${item + 20}/600/400/`"
                                 alt="cover">
                          </div>
                          <div class="text-box">
                            <div class="title">
                              踏遍千山万水，行走在世界的怀抱。旅游是我心中永不停歇的冒险！我喜欢追逐风景，感受异域文化的魅力.
                            </div>
                          </div>
                        </div>
                      </div>
                      <div class="new-block"  @click="goToPage('/blog')">
                        <div class="inner-box">
                          <div class="image">
                            <img class="lazy-image" v-bind:data-src="`https://picsum.photos/id/400/400/`"
                                 alt="Lazy Loaded Image">
                          </div>
                          <div class="over-box">
                            <div class="hvr-lower blog-more">
                              <div class="work-info-icon"><i class="iconfont icon-click"></i></div>
                              <div class="work-info-title">MORE</div>
                            </div>
                          </div>
                        </div>
                      </div>
                    </div>
                  </div>
                </section>-->


        <!-- <section class="connect c-mt-40 c-mb-40" id="contact">
          <ZySectionHeader title="给我留言" titleNum="06"/>
          <p class="message-tips">留下你的足迹，让我知道你在这里看过我的留言板。</p>
          <div class="connect-box">
            <div class="contact-form">
              <ZyForm @submitForm="submitMessage"/>
            </div>
            <ul class="contact-basic">
              <li class="basic-item" v-for="item in state.messageList" :key="item._id">
                <a-avatar
                    :size="40"
                    :src="item.userInfo[0].avatar"
                    alt="匿名"/>
                <a-avatar :size="40" v-if="!item.userInfo[0].avatar">
                  <template #icon>
                    <i style="font-size: 1.6rem" class="iconfont icon-customer-bussinessman"></i>
                  </template>
                </a-avatar>
                <div class="item-r">
                  <p class="r-t">
                    <span class="r-t-name">{{ item.userInfo[0].nickname }}</span>
                    <span class="author" v-if="item.userInfo[0].username==='admin'"></span>
                    <span class="r-t-time">{{
                        TimeUtils.formatRelativeTime(item.createdAt)
                      }}</span></p>
                  <p class="r-desc"> {{ item.content }} </p>
                </div>
              </li>
              <li class="more-msg" @click="goToPage('/contact')">
                <i class="iconfont icon-click"></i> 查看更多
              </li>
            </ul>
          </div>
        </section> -->
      </section>
      <WorldMap/>
      <ZyModal :minWidth="350" :show="state.show.work" title="项目详情" key="ViewUserInfo" @close="close">
        <WorkDetail :viewData="state.viewData"/>
      </ZyModal>
    </section>
  </section>
</template>


<script setup>
import {onMounted, onBeforeUnmount, nextTick, ref, watch, reactive} from 'vue';
import Intro from "./components/intro.vue";
import Zy3DCardList from "../../components/common/Zy3DCardList.vue";
import {useMenusStore} from '../../stores/menus'
import ZyModal from "../../components/common/ZyModal.vue";
import WorkDetail from "../../components/common/work-detail.vue";
import WorldMap from "./components/world-map.vue";
import ExperienceMap from "./components/experience-map.vue";
import {goToPage} from "../../libs/util.router";
import lazyLoadImages from "../../libs/util.lazyLoad";
import {useRouter} from 'vue-router'
import observeAndAnimate from "../../libs/util.viewportObserve";
import ZySectionHeader from "../../components/common/ZySectionHeader.vue";
import ZyForm from "../../components/common/ZyForm.vue";
import ArticleSection from "./components/article-section.vue";
import ExperienceStep from "./components/experience-step.vue";
import {portfoliosList} from "../../api/modules/api.portfolios";
import {messagesCreate, messagesList} from "../../api/modules/api.messages";
import {TimeUtils} from "../../libs/util.time";
import setting from "../../setting";

const router = useRouter()
const menusAction = useMenusStore()

const state = reactive({
  scrollHeight: 0,
  bannerWidth: 100,
  titleAnimation: false,
  textAnimation: false,
  show: {
    work: false
  },
  portfoliosQuery: {
    params: {
      recommended: true,
      status: true,
    },
    pagination: {
      current: 1,
      pageSize: 5,
    },
  },
  portfoliosData: [
    {
        "_id": "64d2f43a97ad53aea60d4ef1",
        "title": "个人博客完整版",
        "cover": "https://img0.baidu.com/it/u=3240131412,3050737635&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
        "abstract": "😜博客全栈系统，个人blog+vue2 + node.js + express +sequalize+ mysql+uniapp 包含前端博客展示、后台管理、node后端服务。包括前后台完整基础功能，微信小程序，H5，web前台站点一键置灰，配置新年特效，支持移动端适配,excel数据导入/导出，sql文件已附上，整套博客系统开箱即用,已完成代码生成器，权限模块，菜单管理等等",
        "content": "\n\n\n<br />\n\n<p align=\"center\">\n  <a href=\"https://gitee.com/Z568_568/mango-blog-system.git\">\n    <img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546637478.png\" alt=\"Logo\" width=\"100\" height=\"80\">\n  </a>\n \n<h3 align=\"center\">\" 🔥 MG'Blog \"</h3>\n  <p align=\"center\">\n    一个 \"开箱即用\" 个人博客全栈系统项目！\n    <br />\n    <a href=\"https://gitee.com/Z568_568/all-blog-sys\" target=\"_blank\"><strong>探索本项目的源码 »</strong></a>\n    <br />\n    <br />\n    <a href=\"http://blog.zhouyi.run/#/\" target=\"_blank\"> 👀 前台预览</a>\n    ·\n    <a href=\"http://admin.blog.zhouyi.run/#/index\" target=\"_blank\"> 👀 管理端预览</a>\n</p>\n\n</p>\n\n#### 🥯 小程序预览\n\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546612429.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546612429.png\" alt=\"1691546612429.png\" width = \"400\" height = \"150\">\n</a>\n\n##### 🥯 QQ群：529675917 由于很多小伙伴对项目的启动安装有问题不明白，可以添加QQ群和大家一起交流解决相关问题哈\n\n\n\n#### 🥯 介绍\n\n>  芒果’个人博客系统，包括前后台完整基础功能，小程序，简洁的web前台站点一键配置，响应式；\n>  管理端常用增·查·改页面代码自动生成即可，文章统计归档、数据excel批量导入/导出，sql文件已附上，开箱即用，如果对你有帮助，留个 **star⭐⭐** 再走呗\n- ⭐项目面向前端学习node.js，mysql等后端基础和小程序学习者\n- ⭐有好的建议欢迎交流学习 1840354092@qq.com\n- ⭐项目启动安装有问题可以留言，会及时解答\n\n```\n   前台：Gblog \n   微信小程序：uniApp + uView \n   管理端：d2-admin \n   Node服务端: express + 数据库ORM（sequelize框架）\n```\n<!-- PROJECT SHIELDS -->\n\n[![star](https://gitee.com/Z568_568/all-blog-sys/badge/star.svg?theme=dark)](https://gitee.com/Z568_568/all-blog-sys/stargazers)\n[![fork](https://gitee.com/Z568_568/all-blog-sys/badge/fork.svg?theme=dark)](https://gitee.com/Z568_568/all-blog-sys/members)\n\n<!-- PROJECT LOGO -->\n\n#### 其他可能需要的资源 \n\n>[✨Vue3-Antd-Plus基于Vue3、Vite、JavaScript、管理后台完整开发模板](https://gitee.com/Z568_568/vue3-antd-plus.git)\n\n>[ZY.Hexo.Blog响应式简约清爽款个人博客](https://gitee.com/Z568_568/zy-hexo-blog.git)\n\n>[轻量级个人文件管理、图床管理服务系统](https://gitee.com/Z568_568/zy.files.sys.git)\n\n>[node+mongodb开发REST API 的轻量级样板 ✨推荐](https://gitee.com/Z568_568/node.mongodb)\n\n>[node+mysql后端api基础服务模板](https://gitee.com/Z568_568/zy-express-sequelize-mysql)\n\n\n***\n\n#### 功能列表及更新\n\n- [x] 用户管理\n- [x] 菜单管理\n- [x] 角色管理 ⛷\n- [x] 文章管理\n- [x] 评论管理\n- [x] 代码生成 ⛷\n- [x] 私信邮件回复\n- [x] 微信小程序 ⛷\n- [x] Excel数据导入/导出 ⛷\n- [x] 生成Echart图表 ⛷\n- [x] 访客管理记录\n- [x] 我的世界\n- [x] 🎈博客在线留言（新增）\n- [x] 🎈站点管理（新增配置新年灯笼）\n- [x] 🎈前台归档管理（新调整）\n- [x] ⛏【已修复 2023/04/19】：管理端添加博文不填标签增加失败 \n- [x] ⛏【已修复 2023/04/19】：管理端删除菜单的错误\n- [x] ⛏【已修复 2023/04/19】：服务端博文标签非空处理 \n- [x] ⛏【已修复 2023/04/19】：客户端分类查询不出非推荐文章 \n- [x] ⛏【已增加 2023/04/19】：管理端访客页的地址模糊查询\n- [x] ⛏【已增加 2023/04/19】：客户端文章详情的相关文章 \n- [x] 更多请查看示例链接...\n\n#### 接口文档\n\n> 方式1. <a href=\"https://console-docs.apipost.cn/preview/85df1005c24df829/b25c320b5df19b98\" target=\"_blank\"> 👀 查看在线接口文档</a> \n\n\n> 方式2. 👀 项目启动后 访问 swagger-ui 接口文档\n\n#### 项目安装启动教程\n\n\n> [安装启动视频教程](https://www.bilibili.com/video/BV1wY411d7s6/?share_source=copy_web&vd_source=3f6515a9fd6d4dc4f53ed5b3697eaea4)\n\n\n``` js\n\n1.依赖安装: 微信小程序 mg-mini | 前台client | 管理端admin | 服务端 server -`npm install`\n\n2.启动项目:  前台client- npm run serve \n           前台微信小程序 - HBuilder 编辑器编译-微信小程序运行\n           管理端admin - npm run dev \n           服务端 server - nodemon app （热启动） 或者 node app\n\n3.服务端启动前准备: \n            3.1 建库: mg_db  建表:运行sql文件到 mg_db 加载数据表\n            3.2 在 mg-server/config/db.config.js 配置数据库信息\n            3.3 启动成功示例： \n                    项目启动成功: http://localhost:5222\n                    接口文档地址: http://localhost:5222/swagger\n\n4.管理端登录账号密码 ：\n            4.1 访客：editor  123456   超级管理员：admin  123456\n```\n\n#### 项目截图\n\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546535717.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546535717.png\" alt=\"1691546535717.png\" width=\"100%\">\n</a>",
        "sourceUrl": "https://gitee.com/Z568_568/all-blog-sys.git",
        "demoUrl": "http://blog.zhouyi.run/#/",
        "category": "博客",
        "framework": "vue2 + node.js + express +sequalize+ mysql+uniapp",
        "recommended": true,
        "status": true,
        "createdAt": "2023-08-09T02:04:42.429Z",
        "updatedAt": "2023-08-09T09:26:40.085Z"
    },
    {
        "_id": "64d2f38497ad53aea60d4edf",
        "title": "Vue3-Antd-Plus",
        "cover": "https://img0.baidu.com/it/u=3240131412,3050737635&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
        "abstract": "👍 提供了一个基于最新的技术栈（Vue 3、Vite、Ant Design Vue 3、JavaScript、Pinia、Hooks和vue-router）的完整开发模板，旨在帮助初学者更快地入门并加入团队开发。该模板包含了一系列功能模块，如大屏展示、自定义主题、角色用户、菜单授权、数据权限和系统参数等，并且所有模块都经过了完整的组件封装",
        "content": "# ZY·Admin【完整版】 Vue3-Antd-Plus (文档更新中)\n\n<p align=\"center\">\n  <a href=\"https://gitee.com/Z568_568/mango-blog-system.git\">\n    <img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546343361.png\" alt=\"Logo\" width=\"150\" height=\"210\">\n \n  </a>\n\n<h3 align=\"center\">\" 🔥 Vue3-Antd-Plus \"</h3>\n  <p align=\"center\">\n    基于 Vue3 + js 现代化的管理系统【完整版】\n    <br />\n    <a href=\"https://gitee.com/Z568_568/vue3-antd-plus.git\" target=\"_blank\"><strong>探索本项目的源码 »</strong></a>\n    <br />\n\n[comment]: <> (<a href='https://gitee.com/Z568_568/ZY-Admin/stargazers'><img src='https://gitee.com/Z568_568/ZY-Admin/badge/star.svg?theme=dark' alt='star'></img></a>)\n\n[comment]: <> (<a href='https://gitee.com/Z568_568/ZY-Admin/members'><img src='https://gitee.com/Z568_568/ZY-Admin/badge/fork.svg?theme=dark' alt='fork'></img></a>)\n</p>\n</p>\n\nVue3-Antd-Plus是一个现代化的管理系统，提供了一系列功能丰富的组件和工具，帮助开发者快速搭建和开发管理后台应用。\n\n**基于 Vue 3 + JavaScript + Pinia +Vite + Ant Design Vue 构建 管理后台+web前台+Node后端代码一整套**  \n\n 做这个项目主要原因：全网大都是 Vue3 + TypeScript 版本的,so so 决定做一个JavaScript版本的供大家使用\n\n![Description](http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546282594.png)\n\n\n---\n\n\n## 截图(管理后台+web前台)\n![Description](http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546282594.png)\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546382159.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546382159.png\" alt=\"1691546382159.png\" width=\"100%\">\n</a>\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546404541.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546404541.png\" alt=\"1691546404541.png\" width=\"100%\">\n</a>\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546426903.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546426903.png\" alt=\"1691546426903.png\" width=\"100%\">\n</a>\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546440411.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546440411.png\" alt=\"1691546440411.png\" width=\"100%\">\n</a>\n\n### 功能：\n\n*   [x] 前台端- 整体框架已搭建好\n*   [x] 前台端- 接口已经接入\n*   [x] 前台端- axios全局统一错误处理\n*   [x] 管理端- 大屏数据可视化\n*   [x] 管理端- 集成各类富文本编辑器\n*   [x] 管理端- 自定义主题、菜单权限、按钮权限\n*   [x] 管理端- 登录、注册、菜单、tabs顶栏菜单、全局搜索菜单\n*   [x] 管理端- 用户管理、角色管理、权限管理、自定义指令权限判断\n*   [x] 管理端- 用户操作日志项目代码生成器（前后端代码文件）、图标选择器\n*   [x] 管理端- 错误统一处理\n*   [x] 管理端- 表格导入、导出、下载\n*   [x] 管理端- 图片文件音频上传、下载、预览...\n*   [x] 服务端- 项目结构清晰\n*   [x] 服务端- 集成邮件发送、定时器任务、统一响应数据格式\n*   [x] 服务端- JWT验证、接口数据权限验证、角色权限验证\n*   [x] 服务端- express-validator统一的参数验证\n*   [x] 服务端- 接口日志记录、表格解析等等...\n\n\n## 功能特性\n\n- 使用 Vue 3 和 Vite 构建，具备高效的开发体验和优秀的性能表现\n- 集成了 Ant Design Vue 组件库，提供美观的 UI 界面和丰富的组件选项 和主题切换\n- 使用 Vue Router 实现路由管理，支持多层级路由和动态路由\n- 使用 Axios 处理 HTTP 请求，与后端进行数据交互\n- 集成 ECharts 图表库，展示数据统计和可视化效果\n- 使用 Pinia 进行状态管理，提供了一种响应式的数据流方案\n- 集成 Tinymce 富文本编辑器和 Vditor Markdown 编辑器，满足不同的编辑需求\n- 使用 hotkeys-js 提供快捷键支持，增强用户操作体验\n- 使用 Lodash 提供常用工具函数，简化开发流程\n- 集成了测试工具集 @vue/test-utils 和 vitest，方便进行单元测试\n- 更多....\n\n#### 我的其他开源项目\n>[😜博客全栈系统 vue2 + node.js](https://gitee.com/Z568_568/all-blog-sys.git)\n \n>[个人文件管理+图床管理服务系统](https://gitee.com/Z568_568/zy.files.sys.git)\n \n>[node+mysql后端api基础服务模板](https://gitee.com/Z568_568/zy-express-sequelize-mysql)\n\n>[node+mongodb开发REST API 的轻量级样板](https://gitee.com/Z568_568/node.mongodb)\n\n\n## 快速开始\n\n1. 克隆本仓库到本地\n\n   ```\n   https://gitee.com/Z568_568/vue3-antd-plus.git\n   ```\n\n2. admin/client/server安装依赖\n\n   ```\n   npm install\n   ```\n\n3. admin/client/server本地启动\n\n   ```\n   npm run dev\n   ```\n\n4. 打包生产环境\n\n   ```\n   npm run build\n   ```\n## admin添加路由页面\n\n```\n/**\n * 在主框架内显示\n * 路由配置说明\n * {\n      path: '/dir-demo-info',    // 页面地址（唯一）\n      name: 'dir-demo-info',     // 页面名称（唯一）\n      hidden: false,              // 隐藏（不展示在侧边栏菜单）\n      meta: {\n          title: '用户管理',       // 页面标题\n          icon: 'yonghuguanli',  // 页面图标\n          cache: true,          // 页面是否进行缓存 默认true\n          link: false,           // 页面是否是外链 默认false\n          frameSrc: false,       // 页面是否是内嵌 默认false\n          requiresAuth: true,   // 页面是否是需要登录 默认true\n          perms: [               // 页面的操作的权限列表\n              'sys:user:list',   // 查询\n              'sys:user:create', // 增加\n              'sys:user:update', // 更新\n              'sys:user:delete', // 删除\n          ],\n      },\n      component: () => import('@/views/sys/user/dir-user-info.vue'),\n   }\n *\n */\n```\n \n....\n\n\n## 贡献\n\n欢迎对Vue3-Antd-Plus项目的改进和完善，如果您发现任何错误或有任何建议，请随时提交问题和拉取请求。\n\n## 版权\n\nVue3-Antd-Plus是一个开源项目，根据MIT许可证发布。有关更多信息，请参阅LICENSE文件。\n\n\n\n",
        "sourceUrl": "https://gitee.com/Z568_568/vue3-antd-plus.git",
        "demoUrl": "https://gitee.com/Z568_568/vue3-antd-plus.git",
        "category": "后台管理系统、大屏数据可视化",
        "framework": "Vue 3、Vite、Ant Design Vue 3、JavaScript、Pinia、Hooks和vue-router",
        "recommended": true,
        "status": true,
        "createdAt": "2023-08-09T02:01:40.456Z",
        "updatedAt": "2023-08-09T02:16:08.554Z"
    },
    {
        "_id": "64d2f28997ad53aea60d4ec7",
        "title": "个人文件管理+图床管理服务系统",
        "cover": "https://img0.baidu.com/it/u=3240131412,3050737635&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
        "abstract": "🎉轻量级个人文件管理、图床管理服务系统，对文本文件、图片、视频、音频、音乐等各类文件的存储管理，基于node.js、mysql、vue2实现。内置用户登录和其他相关接口可扩展功能",
        "content": "# 个人文件管理+图床管理服务系统\n\n#### 项目介绍\n\n---\n🎉开源轻量级个人文件管理、图床管理服务系统，对文本文件、图片、视频、音频、音乐等各类文件的存储管理支持多图上传等功能，基于node.js、mysql、vue2实现。内置用户登录和其他相关接口可扩展功能\n\n[🌍项目源码](https://gitee.com/Z568_568/zy.files.sys.git)\n\n[🌍在线预览demo：http://files.zhouyi.run/#/](http://files.zhouyi.run/#/)\n\n#### 项目截图\n\n---\n![Description](http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546113455.png)\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546169339.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546169339.png\" alt=\"1691546169339.png\" width=\"100%\">\n</a>\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546174433.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546174433.png\" alt=\"1691546174433.png\" width=\"100%\">\n</a>\n\n#### 安装教程\n\n---\n\n1. clone代码\n\n`git clone https://gitee.com/Z568_568/zy.files.sys.git`\n\n2. client安装启动 **客户端操作口令：amdin**\n\n```js\ncd client\nnpm i\nnpm run serve\n```\n\n3. server安装启动\n\n- 新建数据库 `mg_open`\n- 找到 `server/sql/mg_open.sql` 并且运行sql文件\n- 找到 `server/config/index.js` 配置数据库\n\n```js\ncd server\nnpm i\nnodemon app\n```\n\n4. 测试功能\n\n- 上传文件后会在 server 端  `server/uploads_files/files` 中查看该文件\n\n#### 关于作者\n\n---\n创建和维护由\n\n- [@ZY_GITEE](https://gitee.com/Z568_568)\n- [@ZY_GITHUB](https://github.com/ZHYI-source)\n- 想咨询其他或合作请发我邮箱1840354092@qq.com\n- 到我主页留言 [http://www.zhouyi.run](http://www.zhouyi.run/#/About)\n- 我的博客站点 [http://blog.zhouyi.run](http://blog.zhouyi.run/#/)\n\n#### 感谢作者\n\n如果该项目对你有帮助的话 可以通过扫下面二维码打赏来感谢我的努力和花费的时间来创建这个有用的项目。\n\n<div>\n   <a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546198698.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546198698.png\" alt=\"1691546198698.png\" width=\"100\">\n</a> \n   <a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546208890.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691546208890.png\" alt=\"1691546208890.png\" width=\"100\">\n</a>\n</div>\n",
        "sourceUrl": "https://gitee.com/Z568_568/zy.files.sys.git",
        "demoUrl": "http://files.zhouyi.run",
        "category": "文件管理",
        "framework": "node.js、mysql、vue2",
        "recommended": true,
        "status": true,
        "createdAt": "2023-08-09T01:57:29.791Z",
        "updatedAt": "2023-08-09T02:16:03.719Z"
    },
    {
        "_id": "64d2f1e097ad53aea60d4eb1",
        "title": "个人主页模板ZY-Portofolio",
        "cover": "https://img0.baidu.com/it/u=3240131412,3050737635&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
        "abstract": "基于vue3+js实现个人主页模板ZY-Portofolio",
        "content": "\n# zy-portofolio\n\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545619525.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545619525.png\" alt=\"1691545619525.png\" width=\"100%\">\n</a>\n\n## Project setup\n```\nnpm install\n```\n\n### Compiles and hot-reloads for development\n```\nnpm run serve\n```\n\n### Compiles and minifies for production\n```\nnpm run build\n```\n\n### Lints and fixes files\n```\nnpm run lint\n```\n\n### Customize configuration\nSee [Configuration Reference](https://cli.vuejs.org/config/).\n",
        "sourceUrl": "https://gitee.com/Z568_568/zy-portofolio.git",
        "demoUrl": "https://gitee.com/Z568_568/zy-portofolio.git",
        "category": "个人主页",
        "framework": "vue3+js",
        "recommended": true,
        "status": true,
        "createdAt": "2023-08-09T01:54:40.202Z",
        "updatedAt": "2023-08-09T02:16:13.879Z"
    },
    {
        "_id": "64d2ef7797ad53aea60d4e7f",
        "title": "ZY.Node.Mongodb",
        "cover": "https://img0.baidu.com/it/u=3240131412,3050737635&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
        "abstract": "基于 Node.js、Express.js 和 MongoDB 通过Mongoose驱动进行 REST API 开发的轻量级样板。集成了Swagger UI、JWT、session、发送邮箱验证、日志管理、统一的预定义状态码响应格式等，对于为前端平台构建纯净的Web API非常有用。",
        "content": "# ZY.Node.Mongodb \n\n- https://gitee.com/Z568_568/node.mongodb.git\n\n- https://github.com/ZHYI-source/ZY.Node.Mongodb.git\n\n#### 项目介绍\n\n---\n- 基于 Node.js、Express.js 和 MongoDB 通过Mongoose驱动进行 REST API 开发的轻量级样板。\n  集成了Swagger UI、JWT、session、发送邮箱验证、日志管理、统一的预定义状态码响应格式等，对于为前端平台构建纯净的Web API非常有用。\n\n- 该项目我尝试做出轻松维护代码结构的项目样板，因为任何初学者也可以采用该流程并开始构建API。 \n\n- 项目开放，可以提出建议、错误的issues。\n\n\n#### 项目特点\n\n---\n\n- 轻量级Node.js项目提供Restful API\n- 数据库采用 Mongodb, 通过Mongoose驱动。\n- CRUD操作示例\n- 跨域处理\n- 日志管理\n- 具有恰当的状态代码的预定义响应结构\n- 全局错误处理\n- 增加express-validator请求参数校验\n- jwt验证 用户权限中间件分离\n- 基本身份验证（采用bcrypt单向Hash加密算法加密密码进行注册/登录）\n- Token生成和校验请求头的authorization \n- 集成swagger-ui\n- 增加邮件验证码通知\n- session 验证码校验\n- 采用jest 接口单元测试\n- 集成定时任务\n\n\n#### 如何获得并运行项目：\n\n---\n\n> 首先确保您系统中安装了[Mongodb](http://www.mongodb.org/)，和[Nodejs](http://nodejs.org/ \"Nodejs\")，一起准备完善之后。按照如下操作。\n> 有的同学启动会报错可能是依赖包的版本问题需要注意\n> 我的环境配置供参考 \n> - Node.js 14.18.1+ \n> - MongoDB 5.1+\n\n**1，clone代码**\n\n >  `git clone https://gitee.com/Z568_568/node.mongodb.git`\n \n**2，安装依赖**\n\n >  `npm install`\n\n**3，启动程序**\n\n >  `开发环境：npm run dev  基于 nodemon 热更新`\n >  `生产环境：npm run start`\n\n**4，启动成功示例**\n\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545365431.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545365431.png\" alt=\"1691545365431.png\" width=\"100%\">\n</a>\n\n#### 如何增加新的model\n\n---\n只需在 `/models/v1/mapping/` 中创建一个新文件，\n然后在控制器`/controllers/v1/`中创建一个对应新模型的新控制器的并使用。\n\n#### 如何增加新的路由router\n\n---\n只需在 `/routes/v1/` 中创建一个新文件，并且引入它对应的controllers进行使用，routes下面的文件 将被 `mount-routes`插件自动解析并以文件名作为api根路径，\n开发环境下会打印在终端上：\n\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545405853.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545405853.png\" alt=\"1691545405853.png\" width=\"100%\">\n</a>\n\n#### 如何增加新的控制器\n\n---\n只需在 `/controllers/v1/` 中创建一个新文件即可，并且引入相关模型进行使用\n\n\n#### 如何理解内置的登录注册逻辑\n\n```js\n\n/*\n* TODO: 注册登录大概逻辑：\n*       1.用户注册 - 用户信息入库 - 发送验证码 - 校验验证码\n*                                   |\n*                           验证码发送失败、验证码失效或者校验失败 - 重新发送或输入验证码 - 校验验证码\n*   *\n*       2.用户登录 -（账号、密码、验证状态都校验通过）- 发Token\n*                       |\n*                 验证状态不通过 - 重新校验验证码/重发验证码 - 校验验证码 - 发Token\n* */\n\n```\n\n#### 项目结构\n\n---\n\n```sh\n.\n├── app.js                  //入口文件\n├── package.json            //依赖配置文件\n├── .env.development        //开发环境配置\n├── .env.production         //生产环境配置\n├── config                  //项目配置\n│   ├── db.config.js\n│   ├── swagger.config.js\n│   └── ...\n├── controllers             //控制模块（业务处理）\n│   └── v1\n│       ├── UserController.js\n│       └── ...\n├── models                  //模型模块（建表）\n│   └── v1\n│       ├── user.test.js        /模型统一导出\n│       └── mapping\n│           ├──UserModel.js\n│           └── ...\n├── routes                  //路由（配置实际API地址路径）\n│     └── v1\n│         ├── user.test.js\n│         ├── user.js\n│         └── ...\n├── db                      //mongodb数据库连接\n│   ├── user.test.js              \n│   └── ...\n├── middlewares             //中间件\n│   ├── jwt.js\n│   ├── permissions.js\n│   ├── session.js\n│   └── ...\n├── logs                    //日志\n│   ├── info.log\n│   ├── error.log\n│   └── ...\n└── utils                   //辅助工具\n    ├── utils.apiResponse.js\n    ├── utils.mailer.js.js\n    └── ...\n```\n\n#### 关于作者\n\n---\n创建和维护由\n - [@ZY_GITEE](https://gitee.com/Z568_568) \n - [@ZY_GITHUB](https://github.com/ZHYI-source)\n - 想咨询其他或合作请发我邮箱1840354092@qq.com\n - 到我主页留言[http://www.zhouyi.run](http://www.zhouyi.run/#/About)\n - 我的博客站点[http://blog.zhouyi.run](http://blog.zhouyi.run/#/)\n\n#### 感谢作者\n如果该项目对你有帮助的话 可以通过扫下面二维码打赏来感谢我的努力和花费的时间来创建这个有用的项目。\n\n<div>\n   <img src=\"public/md/zfb.jpg\" width=\"100\"> \n   <img src=\"public/md/vx.jpg\" width=\"100\"> \n</div>\n\n#### License\n\n---\n\n[MIT](https://choosealicense.com/licenses/mit/)\n\n```lc\nMIT License\n\nCopyright (c) 2023 周Y\n\nPermission is hereby granted, free of charge, to any person obtaining a copy\nof this software and associated documentation files (the \"Software\"), to deal\nin the Software without restriction, including without limitation the rights\nto use, copy, modify, merge, publish, distribute, sublicense, and/or sell\ncopies of the Software, and to permit persons to whom the Software is\nfurnished to do so, subject to the following conditions:\n\nThe above copyright notice and this permission notice shall be included in all\ncopies or substantial portions of the Software.\n\nTHE SOFTWARE IS PROVIDED \"AS IS\", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR\nIMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,\nFITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE\nAUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER\nLIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,\nOUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE\nSOFTWARE.\n\n```\n\n\n \n",
        "sourceUrl": "https://gitee.com/Z568_568/node.mongodb.git",
        "demoUrl": "https://gitee.com/Z568_568/node.mongodb.git",
        "category": "MongoDB",
        "framework": "Node.js、Express.js、MongoDB",
        "recommended": true,
        "status": true,
        "createdAt": "2023-08-09T01:44:23.703Z",
        "updatedAt": "2023-08-09T01:44:23.703Z"
    },
    {
        "_id": "64d2ef7797ad53aea60d4e7f",
        "title": "ZY.Node.Mongodb",
        "cover": "https://img0.baidu.com/it/u=3240131412,3050737635&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=500",
        "abstract": "基于 Node.js、Express.js 和 MongoDB 通过Mongoose驱动进行 REST API 开发的轻量级样板。集成了Swagger UI、JWT、session、发送邮箱验证、日志管理、统一的预定义状态码响应格式等，对于为前端平台构建纯净的Web API非常有用。",
        "content": "# ZY.Node.Mongodb \n\n- https://gitee.com/Z568_568/node.mongodb.git\n\n- https://github.com/ZHYI-source/ZY.Node.Mongodb.git\n\n#### 项目介绍\n\n---\n- 基于 Node.js、Express.js 和 MongoDB 通过Mongoose驱动进行 REST API 开发的轻量级样板。\n  集成了Swagger UI、JWT、session、发送邮箱验证、日志管理、统一的预定义状态码响应格式等，对于为前端平台构建纯净的Web API非常有用。\n\n- 该项目我尝试做出轻松维护代码结构的项目样板，因为任何初学者也可以采用该流程并开始构建API。 \n\n- 项目开放，可以提出建议、错误的issues。\n\n\n#### 项目特点\n\n---\n\n- 轻量级Node.js项目提供Restful API\n- 数据库采用 Mongodb, 通过Mongoose驱动。\n- CRUD操作示例\n- 跨域处理\n- 日志管理\n- 具有恰当的状态代码的预定义响应结构\n- 全局错误处理\n- 增加express-validator请求参数校验\n- jwt验证 用户权限中间件分离\n- 基本身份验证（采用bcrypt单向Hash加密算法加密密码进行注册/登录）\n- Token生成和校验请求头的authorization \n- 集成swagger-ui\n- 增加邮件验证码通知\n- session 验证码校验\n- 采用jest 接口单元测试\n- 集成定时任务\n\n\n#### 如何获得并运行项目：\n\n---\n\n> 首先确保您系统中安装了[Mongodb](http://www.mongodb.org/)，和[Nodejs](http://nodejs.org/ \"Nodejs\")，一起准备完善之后。按照如下操作。\n> 有的同学启动会报错可能是依赖包的版本问题需要注意\n> 我的环境配置供参考 \n> - Node.js 14.18.1+ \n> - MongoDB 5.1+\n\n**1，clone代码**\n\n >  `git clone https://gitee.com/Z568_568/node.mongodb.git`\n \n**2，安装依赖**\n\n >  `npm install`\n\n**3，启动程序**\n\n >  `开发环境：npm run dev  基于 nodemon 热更新`\n >  `生产环境：npm run start`\n\n**4，启动成功示例**\n\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545365431.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545365431.png\" alt=\"1691545365431.png\" width=\"100%\">\n</a>\n\n#### 如何增加新的model\n\n---\n只需在 `/models/v1/mapping/` 中创建一个新文件，\n然后在控制器`/controllers/v1/`中创建一个对应新模型的新控制器的并使用。\n\n#### 如何增加新的路由router\n\n---\n只需在 `/routes/v1/` 中创建一个新文件，并且引入它对应的controllers进行使用，routes下面的文件 将被 `mount-routes`插件自动解析并以文件名作为api根路径，\n开发环境下会打印在终端上：\n\n<a href=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545405853.png\" target=\"_blank\">\n<img src=\"http://www.zhouyi.run:3089/v1/common/files/preview/img/1691545405853.png\" alt=\"1691545405853.png\" width=\"100%\">\n</a>\n\n#### 如何增加新的控制器\n\n---\n只需在 `/controllers/v1/` 中创建一个新文件即可，并且引入相关模型进行使用\n\n\n#### 如何理解内置的登录注册逻辑\n\n```js\n\n/*\n* TODO: 注册登录大概逻辑：\n*       1.用户注册 - 用户信息入库 - 发送验证码 - 校验验证码\n*                                   |\n*                           验证码发送失败、验证码失效或者校验失败 - 重新发送或输入验证码 - 校验验证码\n*   *\n*       2.用户登录 -（账号、密码、验证状态都校验通过）- 发Token\n*                       |\n*                 验证状态不通过 - 重新校验验证码/重发验证码 - 校验验证码 - 发Token\n* */\n\n```\n\n#### 项目结构\n\n---\n\n```sh\n.\n├── app.js                  //入口文件\n├── package.json            //依赖配置文件\n├── .env.development        //开发环境配置\n├── .env.production         //生产环境配置\n├── config                  //项目配置\n│   ├── db.config.js\n│   ├── swagger.config.js\n│   └── ...\n├── controllers             //控制模块（业务处理）\n│   └── v1\n│       ├── UserController.js\n│       └── ...\n├── models                  //模型模块（建表）\n│   └── v1\n│       ├── user.test.js        /模型统一导出\n│       └── mapping\n│           ├──UserModel.js\n│           └── ...\n├── routes                  //路由（配置实际API地址路径）\n│     └── v1\n│         ├── user.test.js\n│         ├── user.js\n│         └── ...\n├── db                      //mongodb数据库连接\n│   ├── user.test.js              \n│   └── ...\n├── middlewares             //中间件\n│   ├── jwt.js\n│   ├── permissions.js\n│   ├── session.js\n│   └── ...\n├── logs                    //日志\n│   ├── info.log\n│   ├── error.log\n│   └── ...\n└── utils                   //辅助工具\n    ├── utils.apiResponse.js\n    ├── utils.mailer.js.js\n    └── ...\n```\n\n#### 关于作者\n\n---\n创建和维护由\n - [@ZY_GITEE](https://gitee.com/Z568_568) \n - [@ZY_GITHUB](https://github.com/ZHYI-source)\n - 想咨询其他或合作请发我邮箱1840354092@qq.com\n - 到我主页留言[http://www.zhouyi.run](http://www.zhouyi.run/#/About)\n - 我的博客站点[http://blog.zhouyi.run](http://blog.zhouyi.run/#/)\n\n#### 感谢作者\n如果该项目对你有帮助的话 可以通过扫下面二维码打赏来感谢我的努力和花费的时间来创建这个有用的项目。\n\n<div>\n   <img src=\"public/md/zfb.jpg\" width=\"100\"> \n   <img src=\"public/md/vx.jpg\" width=\"100\"> \n</div>\n\n#### License\n\n---\n\n[MIT](https://choosealicense.com/licenses/mit/)\n\n```lc\nMIT License\n\nCopyright (c) 2023 周Y\n\nPermission is hereby granted, free of charge, to any person obtaining a copy\nof this software and associated documentation files (the \"Software\"), to deal\nin the Software without restriction, including without limitation the rights\nto use, copy, modify, merge, publish, distribute, sublicense, and/or sell\ncopies of the Software, and to permit persons to whom the Software is\nfurnished to do so, subject to the following conditions:\n\nThe above copyright notice and this permission notice shall be included in all\ncopies or substantial portions of the Software.\n\nTHE SOFTWARE IS PROVIDED \"AS IS\", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR\nIMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,\nFITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE\nAUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER\nLIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,\nOUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE\nSOFTWARE.\n\n```\n\n\n \n",
        "sourceUrl": "https://gitee.com/Z568_568/node.mongodb.git",
        "demoUrl": "https://gitee.com/Z568_568/node.mongodb.git",
        "category": "MongoDB",
        "framework": "Node.js、Express.js、MongoDB",
        "recommended": true,
        "status": true,
        "createdAt": "2023-08-09T01:44:23.703Z",
        "updatedAt": "2023-08-09T01:44:23.703Z"
    }
],
  viewData: {},
  messageQuery: {
    pagination: {
      current: 1,
      pageSize: 5,
    },
  },
  messageList: []
})


const onDev = () => {
  window.alert('抱歉！功能正在开发中...')
}
const close = () => {
  state.show.work = false
}
const viewWorks = (item) => {
  state.viewData = item
  state.show.work = true
}

const downloadResume = () => {
  // alert('简历下载已关闭')
  // 简历 
  // "https://cashier.obs.cidc-rp-12.joint.cmecloud.cn/file/pdf/20260309154800wize8ecpwgzw.pdf"
  window.open("https://cashier.obs.cidc-rp-12.joint.cmecloud.cn/file/pdf/20260309154800wize8ecpwgzw.pdf")
  // 使用downloadFile 方法下载文件 

}
// 实现平滑滚动到锚点的方法
const scrollToSection1 = (id) => {
  const dom = document.getElementById(id)
  dom.scrollIntoView({behavior: 'smooth'});
};

const getPortfolioList = () => {
  portfoliosList(state.portfoliosQuery).then(res => {
    state.portfoliosData = res.data.result || []
  })
}

const submitMessage = (form) => {
  messagesCreate(form).then(res => {
    if (res.status) {
      let info = {
        name: form.name,
        email: form.email,
        website: form.website
      }
      localStorage.setItem('ZY-CLIENT-USERINFO', JSON.stringify(info))
      getMessageList()
    }
  })
}

const getMessageList = () => {
  messagesList(state.messageQuery).then(res => {
    state.messageList = res.data.result
  })
}

// 获取更多留言数据  --不要
// getMessageList()


watch(() => menusAction.page, (val) => {
  if (val) {
    scrollToSection1(val)
  }
})

// 数据更新后使用 nextTick 来确保在 DOM 更新后执行 lazyLoadImages 方法
watch(() => state.portfoliosData, () => {
  nextTick(() => {
    lazyLoadImages();
  })
});

const handleScroll = (e) => {
  // 滚动事件处理逻辑
  state.titleAnimation = window.scrollY - window.innerHeight / 2.2 > 0;
};

// 获取作品集数据 --写死
// getPortfolioList()

onMounted(() => {
  window.addEventListener('scroll', handleScroll);

  observeAndAnimate('.news-block-two', (element) => {
    // 自定义动画效果
    element.style.opacity = 1;
    element.style.transform = 'translateX(0px)';
  });
  observeAndAnimate('.box-item', (element) => {
    // 自定义动画效果
    element.style.opacity = 1;
    element.style.transform = 'translateY(0px)';
  });


  // 懒加载图片
  lazyLoadImages();

})
onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll);
});

</script>


<style lang="scss" scoped>
@import "style/index";


</style>
