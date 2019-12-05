<template>
  <page-view :avatar="avatar" :title="false">
    <a-anchor :affix="false" class="anchor-div">
      <a-anchor-link href="#register" title="游戏安装" />
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
            <p>需要超级会员联系群主小小心情</p>
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
            style="margin-bottom: 24px;"
            :bordered="false"
            title="游戏安装"
            >
            <div style="padding: 20px;">
              <img src="../../assets/icons/lostfile.png" width="300px" height="300px" alt="">
              <p>一般是因为解压时没有关闭杀毒软件，需要找回被删除的文件，Msg.dll</p>
            </div>
          </a-card>

        </a-col>
        <a-col
          :xl="24"
          :lg="24"
          :md="24"
          :sm="24"
          :xs="24"
          id="account">
          <a-card  title="账号信息" :bordered="false">
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
          <a-card  title="加速器" :bordered="false">
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
import axios from 'axios'
import $ from 'jquery'
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
  name: 'Monitor',
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
      radarData: [],
      onlineNumL: null
    }
  },

  created () {

  },
  mounted () {
  },
  methods: {
    getOnlineNum () {
      // axios.get('https://www.aionlegend.im/index.php',{}, {
      //   headers: { Accept: 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3',
      //   referer:'https://cp.aionlegend.im/',
      //   host:'cp.aionlegend.im'
      // }}).then(res => {
      //   console.log(res)
      //   setTimeout(() => {
      //     this.getOnlineNum()
      //   }, 10000)
      // })
//       var url = "https://www.aionlegend.im/index.php";
// //     // 创建script标签，设置其属性
//     var script = document.createElement('script');
//     script.setAttribute('src', url);
// console.log(script);
// document.getElementsByTagName('head')[0].appendChild(script);
// console.log('222')

// let headers = {'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36',
// 'referer': 'https://cp.aionlegend.im',
// 'sec-fetch-mode': 'cors',
// 'sec-fetch-site': 'same-origin',
// 'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3'
// }
//     $.ajax({
//           type: "GET",
//           async: false,
//           url: "https://www.aionlegend.im/index.php",
//           data: {},
//           headers:headers,
//           jsonpCallback:"jsonpCallback",
//           dataType: "jsonp",
//           success: function() { console.log('Success!'); },
//     error: function(res) { console.log(res); },
//       });
//       function jsonpCallback(data) {
//         console.log(data);

//       }
    },
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
