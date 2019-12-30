<template>
  <div class="page-header">
    <div class="page-header-index-wide">
      <s-breadcrumb />
      <div class="detail">
        <div class="main" v-if="!$route.meta.hiddenHeaderContent">
          <div class="row">
            <img v-if="logo" :src="logo" class="logo"/>
            <h1 v-if="title" class="title">{{ title }}</h1>
            <div class="action">
              <slot name="action"></slot>
            </div>
          </div>
          <div class="row">
            <div class="avatar">
              <a-avatar src="/avatar2.jpg" />
            </div>
            <div v-if="this.$slots.content" class="headerContent">
              <slot name="content"></slot>
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
                <a style="display:block;float: left; margin-left: 10px;margin-top:2px;font-size: 14px;" @click="register">邀请注册链接</a>
                <a-popconfirm placement="bottom" okText="确定" cancelText="取消" @confirm="confirm">
                  <template slot="title">
                    <p>点击确认导航至百度云盘分享链接，</p>
                    <p>提取码：kcc7</p>
                    <p>需要超级会员联系群主小小心情 <a href="http://wpa.qq.com/msgrd?v=3&uin=173708480&site=qq&menu=yes" target="_blank">添加好友</a></p>
                  </template>
                  <a style="display:block;float: left; margin-left: 10px;margin-top:2px;font-size: 14px;" >游戏下载</a>
                </a-popconfirm>
              </div>
            </div>
            <div v-if="this.$slots.extra" class="extra">
              <slot name="extra"></slot>
            </div>
          </div>
          <div>
            <slot name="pageMenu"></slot>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Breadcrumb from '@/components/tools/Breadcrumb'

export default {
  name: 'PageHeader',
  components: {
    's-breadcrumb': Breadcrumb
  },
  props: {
    title: {
      type: [String, Boolean],
      default: true,
      required: false
    },
    logo: {
      type: String,
      default: '',
      required: false
    },
    avatar: {
      type: String,
      default: '',
      required: false
    }
  },
  data () {
    return {}
  },
  methods: {
    register () {
      window.open('http://www.aionlegend.net/register.html')
    },
    downLoad () {

    },
    confirm () {
      window.open('https://pan.baidu.com/s/1gdSNpIoM_jGQgBu1IpivBA')
    }
  }
}
</script>

<style lang="less" scoped>
.page-header {
  background: #fff;
  padding: 16px 32px 0;
  border-bottom: 1px solid #e8e8e8;

  .breadcrumb {
    margin-bottom: 16px;
  }

  .detail {
    display: flex;
    /*margin-bottom: 16px;*/

    .avatar {
      flex: 0 1 72px;
      margin: 0 24px 8px 0;

      & > span {
        border-radius: 72px;
        display: block;
        width: 72px;
        height: 72px;
      }
    }

    .main {
      width: 100%;
      flex: 0 1 auto;

      .row {
        display: flex;
        width: 100%;

        .avatar {
          margin-bottom: 16px;
        }
      }

      .title {
        font-size: 20px;
        font-weight: 500;

        font-size: 20px;
        line-height: 28px;
        font-weight: 500;
        color: rgba(0, 0, 0, 0.85);
        margin-bottom: 16px;
        flex: auto;
      }
      .logo {
        width: 28px;
        height: 28px;
        border-radius: 4px;
        margin-right: 16px;
      }
      .content,
      .headerContent {
        flex: auto;
        color: rgba(0, 0, 0, 0.45);
        line-height: 22px;

        .link {
          margin-top: 16px;
          line-height: 24px;

          a {
            font-size: 14px;
            margin-right: 32px;
          }
        }
      }
      .extra {
        flex: 0 1 auto;
        margin-left: 88px;
        min-width: 242px;
        text-align: right;
      }
      .action {
        margin-left: 56px;
        min-width: 266px;
        flex: 0 1 auto;
        text-align: right;
        &:empty {
          display: none;
        }
      }
    }
  }
}

.mobile .page-header {
  .main {
    .row {
      flex-wrap: wrap;

      .avatar {
        flex: 0 1 25%;
        margin: 0 2% 8px 0;
      }

      .content,
      .headerContent {
        flex: 0 1 70%;

        .link {
          margin-top: 16px;
          line-height: 24px;

          a {
            font-size: 14px;
            margin-right: 10px;
          }
        }
      }

      .extra {
        flex: 1 1 auto;
        margin-left: 0;
        min-width: 0;
        text-align: right;
      }

      .action {
        margin-left: unset;
        min-width: 266px;
        flex: 0 1 auto;
        text-align: left;
        margin-bottom: 12px;

        &:empty {
          display: none;
        }
      }
    }
  }
}
</style>
