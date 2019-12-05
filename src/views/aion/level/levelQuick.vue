<template>
  <page-view :avatar="avatar" :title="false">
    <a-anchor :affix="false" class="anchor-div">
      <a-anchor-link href="#register" title="注册" />
      <a-anchor-link href="#account" title="账号相关" />
      <a-anchor-link href="#jiasu" title="加速器" />
      <!-- <a-anchor-link href="#API" title="API">
        <a-anchor-link href="#Anchor-Props" title="Anchor Props" />
        <a-anchor-link href="#Link-Props" title="Link Props" />
      </a-anchor-link> -->
    </a-anchor>
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
            <p>需要超级会员联系群主小小心情 <a href="http://wpa.qq.com/msgrd?v=3&uin=173708480&site=qq&menu=yes" target="_blank">添加好友</a></p>
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
            title="快感体验 "
            :body-style="{ padding: 0 }">
            <div style="padding: 20px;">
              <P>各位新人大家好：</P>
              <P>我是一名和大家一样热爱永恒的玩家K剑，欢迎大家来到俄服NC授权4.6大家庭，希望大家在此可以娱乐游戏，注意身体，开心生活，幸福安康！</P>
              <P>我首先鼓励大家自由体验亚特雷亚各处自然人文风光，但是如果您时间有限，又想快速体验65级满级后与大家下本，PK，竞技场，要塞战的快感，那么我可以帮助大家快速满级，当然了，养家糊口，需要收费，收费如下：</P>
              <P>1-50级，  100元   1天交付 </P>
              <P>50-60级，100元   1天交付 </P>
              <P>60-65级    80元    1天交付</P>
              <P>1-65级     累加280  3天交付</P>
              <P>（备注：此代练前提是，您已经开通好五倍经验，并且我登录您的账号双开服务，如果您需要的是私人VIP带着您打，您上账号升级服务则按一小时50收费，在私人VIP期间，一切听您指挥，按您指导，我专属于您一人）</P>
              <P>祝大家在亚特雷亚玩得愉快~~谢谢大家~~     </P>  
              <a href="http://wpa.qq.com/msgrd?v=3&uin=703690864&site=qq&menu=yes" target="_blank">添加好友</a>       
            </div>
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
