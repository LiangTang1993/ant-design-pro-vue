<template>
  <page-view :avatar="avatar" :title="false">
    <a-anchor :affix="false" class="anchor-div">
      <a-anchor-link href="#jieshao" title="俄服介绍" />
      <a-anchor-link href="#register" title="注册" >
        <a-anchor-link href="#chrome" title="浏览器问题" />
        <a-anchor-link href="#registerHelp" title="注册教程" />
      </a-anchor-link>
      <a-anchor-link href="#download" title="下载游戏一定看" />
      <a-anchor-link href="#account" title="账号相关" />
      <a-anchor-link href="#jiasu" title="加速器" />

    </a-anchor>
    <div slot="headerContent">

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
        <a-col
          :xl="24"
          :lg="24"
          :md="24"
          :sm="24"
          :xs="24"
          id="register">
          <a-card
            class="project-list"
            :loading="loading"
            style="margin-bottom: 24px;"
            :bordered="false"
            title="俄服介绍"
            id="jieshao"
            :body-style="{ padding: 0 }">
            <div style="padding: 20px;">
              <p>群刚建，人比较少攻略完善中，有问必答！</p>
              <p>服务器名称 <span style="color: red;">AionLegend</span></p>
              <p>这个服NC授权了65版本（官网底部有授权标记），开了10年，65版本最少再开2年，现在军装最好一等紫。</p>
              <p style="color: red;">服务器没有PC,外挂，抽奖，Vip等各种影响平衡的东西！</p>
              <p>玩这个游戏需要加速器，推荐腾讯加速器，莫斯科节点，我的延迟150左右.电信光纤</p>
              <p style="color: red;font-size: 22px;">这个游戏点击邀请链接注册账号=拜师，点击注册后师徒都会有奖励，详情看下面！</p>
              <p>现在国人天族多魔族少，但是要塞55开！魔族比较乱热爱魔族的玩家先进群了解下注意事项。</p>
              <p>服务器每天6,16,21点维护15分钟保证服务器不卡</p>
              <p>天族进群新建小号找群主领取基本物资。</p>
            </div>
          </a-card>
        </a-col>
        <a-col
          :xl="24"
          :lg="24"
          :md="24"
          :sm="24"
          :xs="24"
          id="register">
          <a-card
            class="project-list"
            :loading="loading"
            style="margin-bottom: 24px;"
            :bordered="false"
            title="注册须知"
            id="chrome"
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
              <img src="../../assets/icons/guge2.png" alt="" >
              <a-divider></a-divider>
              <div id="registerHelp">
                <h3>注册： <a @click="register">点我注册有福利</a></h3>
                <p>注册成功满级可获得</p>
                <p>闪耀大师30天</p>
                <p>永久坐骑鸡</p>
                <p>永久报警自动拾取宠物</p>
                <p>永久岩浆翅膀外形</p>
                <p style="color: red;font-size: 22px;">领取要求:满级前不得更换电脑登录也不可在此电脑登录其他账号,否则无法领取.</p>
                <p>打开链接后如果长时间都没有自动跳转则手动点击页面中蓝色链接如下图</p>
                <img src="../../assets/icons/yaoqing1.png" width="800px" height="500px" alt="">
                <p>跳转后页面如下</p>
                <img src="../../assets/icons/yaoqing2.png" width="800px" height="500px" alt="">
                <p>输入注册邮箱点击创建，登录邮箱点击收到的邮件右键翻译。邮件可能会卡，卡的时候可能不能正常点击active链接，等网好吧！</p>
                <img src="../../assets/icons/active.png" width="500px" height="700px" alt="">
                <p>至此创建完成</p>
              </div>
            </div>
          </a-card>

        </a-col>
        <a-col
          :xl="24"
          :lg="24"
          :md="24"
          :sm="24"
          :xs="24"
          id="download">
          <a-card :loading="loading" title="游戏下载必看" :bordered="false">
            <p><a style="display:block;float: left; margin-left: 10px;margin-top:2px;font-size: 14px;" >游戏下载</a> 已经汉化过了 </p>
            <img src="../../assets/icons/dwonload1.png" width="600px" height="300" alt="">
            <p>没有超级会员联系群主</p>
            <p>下载注意：</p>
            <p style="font-size: 22px; color: red;">1.杀毒软件全关了！！ 360  腾讯管家之类  删文件！导致进不去游戏 报错如下</p>
            <img src="../../assets/icons/lostfile.png" width="240px" height="100" alt="">
            <p style="font-size: 22px; color: red;">2.解压路径整个路径不能有中文！不能！比如：E:\中文\aion 导致进不去游戏 报错如下</p>
            <img src="../../assets/icons/error2.png" width="240px" height="100" alt="">
            <p></p>
          </a-card>
        </a-col>
        <a-col
          :xl="24"
          :lg="24"
          :md="24"
          :sm="24"
          :xs="24"
          id="account">
          <a-card :loading="loading" title="账号信息" :bordered="false">
            <p>邮箱里面的账号为论坛账号和游戏账号 初始是一样的，<a href="https://forum.aionlegend.im/index.php" target="_blank">点我进入官网</a> </p>
            <img src="../../assets/icons/luntanhome.png" width="800px" height="300px" alt="">
            <p>点击登入</p>
            <img src="../../assets/icons/denglu.png" width="800px" height="400px" alt="">
            <p>登陆成功</p>
            <img src="../../assets/icons/accountinfo1.png" width="800px" height="300px" alt="">
            <img src="../../assets/icons/accountinfo2.png" width="420px" height="400px" alt="">
          </a-card>
        </a-col>
        <a-col
          :xl="24"
          :lg="24"
          :md="24"
          :sm="24"
          :xs="24"
          id="jiasu">
          <a-card :loading="loading" title="加速器" :bordered="false">
            <p>俄服基本必须用加速器才能游戏，登录游戏尝试觉着不行买加速器，推荐使用腾讯加速器，<a href="https://jiasu.qq.com/?ADTAG=sem.baidu.ppc">点击购买</a></p>
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
      window.open('http://www.aionlegend.net/register.html')
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
  .anchor-div{
      position: fixed;
      right: 20px;
      z-index:999;
      padding: 20px;
    }
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
