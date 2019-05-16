<template>
  <section class="uh100 ub ub-ac">
    <div class="hd-con ub ub-ac">
      <a href="home.html" class="hd-logo">
        <img class="uw100 uh100" v-lazy="imgs.logo">
      </a>
      <div class="hd-nav ub-f1 ub mt10">
        <el-tabs v-model="activeName" @tab-click="handleSelect" class="mauto">
          <el-tab-pane v-for="(tab, i) in tabs" :label="tab" :name="tab"></el-tab-pane>
        </el-tabs>
      </div>
      <div>
        <div v-if="!BEARER" class="inline-block">
          <!-- <button class="hd-btn b-blu c-wh" @click="">注册</button> -->
          <el-button type="primary" class="hd-btn" plain @click="">登录</el-button>
        </div>

        <el-dropdown v-else class="inline-block c-blu cur" trigger="click">
          <div class="inline-block">
            <img class="user-avatar" src="https://wpimg.wallstcn.com/f778738c-e4f8-4870-b634-56703b4acafe.gif?imageView2/1/w/80/h/80">
            <i class="el-icon-caret-bottom"></i>
            <span class="c-3">您好，</span>{{BEARER | tel}}
          </div>
          <el-dropdown-menu class="user-dropdown" slot="dropdown">
            <a href="manage.html" class="inlineBlock">
              <el-dropdown-item>
                个人中心
              </el-dropdown-item>
            </a>
            <el-dropdown-item divided>
              <span @click="logout" style="display:block;">登出</span>
            </el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </div>

  </section>
</template>

<script>

  export default {
    name: 'HeadBar',
    data(){
      return {

        imgs: {
          logo: 'https://ans-wer.oss-cn-beijing.aliyuncs.com/pc/text_logo.svg'
        },

        tabs: [ '首页', '搜好仓', '金融服务', '产品服务', '我的好仓', '关于我们', '新闻动态', '加入我们', '后台管理'],
        activeName: '首页'
      }
    },
    components: {

    },
    filters: {
      tel (phone){
        return phone.replace(/(\d{3})\d{4}(\d{4})/, "$1****$2")
      }
    },
    mounted(){
      // console.log(this.BEARER)
    },
    methods: {

      handleSelect(){
        let url = '';
        switch(this.activeName){
          case '首页':
            this.$message({
              showClose: true,
              message: '暂未开放'
            });
            break;
          case '搜好仓':
            // url = 'user.html#/reg';
            break;
        }

        if (url !== ''){

          location.href = url;
        }
      },

      logout() {
        location.reload();
        // this.$store.dispatch('FedLogOut').then(() => {
        //   location.reload() // 为了重新实例化vue-router对象 避免bug
        // })
      }
    }
  }
</script>

<style>
  .hd-con .el-tabs__nav-wrap::after{background-color: #fff;}
</style>
<style scoped>

  .hd-con{width: 1200px; margin: 0 auto;}
  .hd-logo{display: block;width: 130px;height:100%;margin-left: 20px;}
  .hd-nav{height: 50px;}
  .hd-btn{font-size: 13px;padding: 10px 20px;background-color: #fff;cursor: pointer;font-weight: bold;}
  .hd-avator{width: 30px;height: 30px;}


  .hd-con  .user-avatar {
    width: 40px;
    height: 40px;
    border-radius: 10px;
  }
  .hd-con  .el-icon-caret-bottom {
    position: absolute;
    right: -20px;
    top: 15px;
    font-size: 12px;
  }
</style>
