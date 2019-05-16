<template>
  <section class="ft-con f14">
    <div class="ub ub-pc">
      <a :href="nav.href" v-for="nav in navs" class="ft-con-nav">{{nav.name}}</a>
    </div>
    <div class="mt20 tx-c c-9">@2015-2018 北京浩德钢圈科技股份有限公司 版权所有 1.16.0 京ICP备17044625号</div>
  </section>
</template>

<script>
  export default {
    name: 'FootBar',
    data(){
      return {
        navs: [
          { href: '', name: '首页' } ,
          { href: '', name: '搜好仓' } ,
          { href: '', name: '金融服务' } ,
          { href: '', name: '产品服务' } ,
          { href: '', name: '我的好仓' } ,
          { href: '', name: '关于我们' } ,
          { href: '', name: '新闻动态' } ,
          { href: '', name: '加入我们' } ,
          { href: '', name: '后台管理'}
        ]
      }
    },
    computed: {

    }
  }
</script>

<style scoped>
  .ft-con{padding: 35px 0;color:#e5e5e5;background: #20a0ff}
  .ft-con-nav{display: block;width: 120px;color: #fff;font-weight: bold;text-align: center;}
  .ft-con-nav:hover{font-weight: bold;color: #0097ff;}
</style>


