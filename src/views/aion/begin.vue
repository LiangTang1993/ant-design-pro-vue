<template>
  <page-view :avatar="avatar" :title="false">
    <div slot="headerContent">
      <div class="title">NC授权俄服，开服十年，巅峰在线3000+</div>
      <div style="font-size: 20px;height: 20px;">
        <div style="float: left;"><a
          target="_blank"
          href="//shang.qq.com/wpa/qunwpa?idkey=a0d254136ae992173d14cfdb8ba216f8e29b2dedb4e359a5c82550e89c22f75b"><img
            border="0"
            src="//pub.idqqimg.com/wpa/images/group.png"
            alt="永恒之塔俄服一带一路"
            title="永恒之塔俄服一带一路"></a></div>
        <div style="float: left; margin: 2px 10px 0 10px;">941524284</div>
        <a style="display:block;float: left; margin-left: 10px;margin-top:2px;font-size: 14px;" @click="register">注册</a>
        <a-popconfirm placement="bottom" okText="确定" cancelText="取消" @confirm="confirm">
          <template slot="title">
            <p>点击确认导航至百度云盘分享链接，</p>
            <p>提取码：kcc7</p>
            <p>需要会员联系群主小小心情</p>
          </template>
          <a style="display:block;float: left; margin-left: 10px;margin-top:2px;font-size: 14px;" >下载</a>
        </a-popconfirm>

      </div>
    </div>
    <div slot="extra">
      <!-- <a-row class="more-info">
        <a-col :span="8">
          <head-info :title="$t('aion.begin.project')" content="56" :center="false" :bordered="false"/>
        </a-col>
        <a-col :span="8">
          <head-info :title="$t('aion.begin.teamRank')" content="8/24" :center="false" :bordered="false"/>
        </a-col>
        <a-col :span="8">
          <head-info :title="$t('aion.begin.views')" content="2,223" :center="false" />
        </a-col>
      </a-row> -->
    </div>

    <div>
      <a-row :gutter="24">
        <a-col :xl="24" :lg="24" :md="24" :sm="24" :xs="24">
          <a-card
            class="project-list"
            :loading="loading"
            style="margin-bottom: 24px;"
            :bordered="false"
            title="注册须知"
            :body-style="{ padding: 0 }">
            <div style="padding: 20px;">
              <h3>注册推荐使用谷歌浏览器！</h3>
              <p>在谷歌浏览器页面右键选项有翻译成中文选项，可将外语页面翻译为中文。</p>
              <p>首先安装谷歌访问助手，因为是外网，不安装会导致无法登陆。</p>
              <p>最新的安装谷歌访问助手2.3.0版本详细教程，旧方法已失效, 但是网上很多的教程或者安装插件包都已经失效了，因为浏览器现在不支持这么直接拖进去了。</p>
              <p>1.群里下载谷歌访问助手，然后解压。</p>
              <p>2.打开浏览器这里以谷歌浏览器和360急速浏览器为例
                谷歌浏览器：点击右侧三个点点，找到更多工具，扩展中心
                360急速浏览器：点击右侧三个横行，点击工具，管理扩展</p>
              <img src="../../assets/icons/guge.png" alt="" width="500px" height="500px">
              <p>3.点击加载已解压的扩展程序，选择我们刚刚下载解压后的文件夹即可，然后就安装成功了，如果没有显示可以重启一下浏览器</p>
              <a-divider></a-divider>
              <h3>注册： <a @click="register">点我注册</a></h3>
              <p>注册成功满级可获得</p>
              <p>闪耀大师30天</p>
              <p>永久坐骑鸡</p>
              <p>永久报警自动拾取宠物</p>
              <p>永久岩浆翅膀外形</p>
              <p>领取要求:满级前不得更换电脑登录也不可在此电脑登录其他账号,否则无法领取.</p>
              <p>打开链接后如果长时间都没有自动跳转则手动点击页面中蓝色链接如下图</p>
              <img src="../../assets/icons/yaoqing1.png" width="800px" height="500px" alt="">
              <p>跳转后页面如下</p>
              <img src="../../assets/icons/yaoqing2.png" width="800px" height="500px" alt="">
              <p>输入注册邮箱点击创建，登录邮箱点击收到的邮件右键翻译。</p>
              <img src="../../assets/icons/active.png" width="500px" height="700px" alt="">
            </div>
          </a-card>

          <a-card :loading="loading" title="动态" :bordered="false">
            <a-list>
              <a-list-item :key="index" v-for="(item, index) in activities">
                <a-list-item-meta>
                  <a-avatar slot="avatar" :src="item.user.avatar" />
                  <div slot="title">
                    <span>{{ item.user.nickname }}</span>&nbsp;
                    在&nbsp;<a href="#">{{ item.project.name }}</a>&nbsp;
                    <span>{{ item.project.action }}</span>&nbsp;
                    <a href="#">{{ item.project.event }}</a>
                  </div>
                  <div slot="description">{{ item.time }}</div>
                </a-list-item-meta>
              </a-list-item>
            </a-list>
          </a-card>
        </a-col>
      </a-row>
    </div>
  </page-view>
</template>

<script>
import {
  timeFix
} from '@/utils/util'
import {
  mapState
} from 'vuex'

import {
  PageView
} from '@/layouts'
import HeadInfo from '@/components/tools/HeadInfo'
import {
  Radar
} from '@/components'

import {
  getRoleList,
  getServiceList
} from '@/api/manage'

const DataSet = require('@antv/data-set')

export default {
  name: 'Begin',
  components: {
    PageView,
    HeadInfo,
    Radar
  },
  data () {
    return {
      timeFix: timeFix(),
      avatar: '',
      user: {},

      projects: [],
      loading: true,
      radarLoading: true,
      activities: [],
      teams: [],

      // data
      axis1Opts: {
        dataKey: 'item',
        line: null,
        tickLine: null,
        grid: {
          lineStyle: {
            lineDash: null
          },
          hideFirstLine: false
        }
      },
      axis2Opts: {
        dataKey: 'score',
        line: null,
        tickLine: null,
        grid: {
          type: 'polygon',
          lineStyle: {
            lineDash: null
          }
        }
      },
      scale: [{
        dataKey: 'score',
        min: 0,
        max: 80
      }],
      axisData: [{
        item: '引用',
        a: 70,
        b: 30,
        c: 40
      },
      {
        item: '口碑',
        a: 60,
        b: 70,
        c: 40
      },
      {
        item: '产量',
        a: 50,
        b: 60,
        c: 40
      },
      {
        item: '贡献',
        a: 40,
        b: 50,
        c: 40
      },
      {
        item: '热度',
        a: 60,
        b: 70,
        c: 40
      },
      {
        item: '引用',
        a: 70,
        b: 50,
        c: 40
      }
      ],
      radarData: []
    }
  },
  computed: {
    ...mapState({
      nickname: (state) => state.user.nickname,
      welcome: (state) => state.user.welcome
    }),
    userInfo () {
      return this.$store.getters.userInfo
    }
  },
  created () {
    this.user = this.userInfo
    this.avatar = this.userInfo.avatar

    getRoleList().then(res => {
      // console.log('begin -> call getRoleList()', res)
    })

    getServiceList().then(res => {
      // console.log('begin -> call getServiceList()', res)
    })
  },
  mounted () {
    this.getProjects()
    this.getActivity()
    this.getTeams()
    this.initRadar()
  },
  methods: {
    getProjects () {
      this.$http.get('/list/search/projects')
        .then(res => {
          this.projects = res.result && res.result.data
          this.loading = false
        })
    },
    getActivity () {
      this.$http.get('/begin/activity')
        .then(res => {
          this.activities = res.result
        })
    },
    getTeams () {
      this.$http.get('/begin/teams')
        .then(res => {
          this.teams = res.result
        })
    },
    initRadar () {
      this.radarLoading = true

      this.$http.get('/begin/radar')
        .then(res => {
          const dv = new DataSet.View().source(res.result)
          dv.transform({
            type: 'fold',
            fields: ['个人', '团队', '部门'],
            key: 'user',
            value: 'score'
          })

          this.radarData = dv.rows
          this.radarLoading = false
        })
    },
    register () {
      window.open('https://www.aionlegend.im/r/?invite=NS1I27')
    },
    downLoad () {

    },
    confirm () {
      window.open('https://pan.baidu.com/share/init?surl=yRMDPjybgT5v3vZDku8awQ')
    }
  }
}
</script>

<style lang="less" scoped>
  .project-list {

    .card-title {
      font-size: 0;

      a {
        color: rgba(0, 0, 0, 0.85);
        margin-left: 12px;
        line-height: 24px;
        height: 24px;
        display: inline-block;
        vertical-align: top;
        font-size: 14px;

        &:hover {
          color: #1890ff;
        }
      }
    }

    .card-description {
      color: rgba(0, 0, 0, 0.45);
      height: 44px;
      line-height: 22px;
      overflow: hidden;
    }

    .project-item {
      display: flex;
      margin-top: 8px;
      overflow: hidden;
      font-size: 12px;
      height: 20px;
      line-height: 20px;

      a {
        color: rgba(0, 0, 0, 0.45);
        display: inline-block;
        flex: 1 1 0;

        &:hover {
          color: #1890ff;
        }
      }

      .datetime {
        color: rgba(0, 0, 0, 0.25);
        flex: 0 0 auto;
        float: right;
      }
    }

    .ant-card-meta-description {
      color: rgba(0, 0, 0, 0.45);
      height: 44px;
      line-height: 22px;
      overflow: hidden;
    }
  }

  .item-group {
    padding: 20px 0 8px 24px;
    font-size: 0;

    a {
      color: rgba(0, 0, 0, 0.65);
      display: inline-block;
      font-size: 14px;
      margin-bottom: 13px;
      width: 25%;
    }
  }

  .members {
    a {
      display: block;
      margin: 12px 0;
      line-height: 24px;
      height: 24px;

      .member {
        font-size: 14px;
        color: rgba(0, 0, 0, .65);
        line-height: 24px;
        max-width: 100px;
        vertical-align: top;
        margin-left: 12px;
        transition: all 0.3s;
        display: inline-block;
      }

      &:hover {
        span {
          color: #1890ff;
        }
      }
    }
  }

  .mobile {

    .project-list {

      .project-card-grid {
        width: 100%;
      }
    }

    .more-info {
      border: 0;
      padding-top: 16px;
      margin: 16px 0 16px;
    }

    .headerContent .title .welcome-text {
      display: none;
    }
  }
</style>
