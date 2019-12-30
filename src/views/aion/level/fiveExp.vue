<template>
  <page-view :avatar="avatar" :title="false">
    <a-anchor :affix="false" class="anchor-div">
      <a-anchor-link href="#chonzhi" title="充值" />
      <a-anchor-link href="#goumai" title="五倍购买" />
    </a-anchor>
    <div slot="headerContent">
    </div>

    <div>
      <a-row :gutter="24">
        <a-col
          :xl="24"
          :lg="24"
          :md="24"
          :sm="24"
          :xs="24"
          id="chonzhi">
          <a-card
            class="project-list"
            :loading="loading"
            style="margin-bottom: 24px;"
            :bordered="false"
            title="充值"
            :body-style="{ padding: 0 }">
            <div style="padding: 20px;">
              <a href="https://cp.aionlegend.im/index.php" target="_blank">点我进入官网</a>
              <p>国内白天登陆官网比较流畅 晚上巨卡 建议大家有什么账号操作都在白天做完</p>
              <img src="../../../assets/icons/cz1.png" width="1100px" height="600" alt="">
              <p>下一步</p>
              <img src="../../../assets/icons/cz2.png" width="800px" height="400" alt="">
              <p>下一步</p>
              <img src="../../../assets/icons/cz3.png" width="800px" height="600" alt="">
              <p>下一步</p>
              <img src="../../../assets/icons/cz4.png" width="800px" height="600" alt="">
            </div>
          </a-card>
        </a-col>
        <a-row :gutter="24">
          <a-col
            :xl="24"
            :lg="24"
            :md="24"
            :sm="24"
            :xs="24"
            id="goumai">
            <a-card
              class="project-list"
              :loading="loading"
              style="margin-bottom: 24px;"
              :bordered="false"
              title="五倍购买"
              :body-style="{ padding: 0 }">
              <div style="padding: 20px;">
                <img src="../../../assets/icons/wupin2.png" width="500px" height="400" alt="">
                <img src="../../../assets/icons/wupin1.png" width="1100px" height="600" alt="">

              </div>
            </a-card>
          </a-col>
        </a-row>
      </a-row></div>
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
