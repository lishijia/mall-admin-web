<template>
  <div class="jj">
    <!-- start top -->
    <div class="jj-header">
      <div style="display: flex;">
        <div class="jj-header-logo">
          <!-- 友迹营销管理平台  游智慧全域旅游管理平台-->
          <img class="jj-header-logo-img" :src="logoUrl">
        </div>
      </div>

      <div class="jj-header-right">
        <div class="jj-header-user-img">
          <img src="../../assets/images/user-icon.png" alt="" class="jj-user-logo">
          <span class="jj-header-text">john</span>
        </div>
        <div class="jj-header-edit-pwd">
          <img src="../../assets/images/edit_pwd.png" alt="修改密码" class="jj-edit-pwd-icon">
        </div>
        <div class="jj-header-logout">
          <img src="../../assets/images/logout.png" alt="退出" class="jj-logout-icon">
        </div>
      </div>

    </div>
    <div class="app-wrapper" :class="classObj">
      <sidebar class="sidebar-container" style="margin-top: 60px;"></sidebar>
      <div class="main-container" style="margin-top: 60px;">
        <navbar></navbar>
        <app-main></app-main>
      </div>
    </div>
  </div>
</template>

<script>
import { Navbar, Sidebar, AppMain } from './components'
import ResizeMixin from './mixin/ResizeHandler'

export default {
  data(){
    return {
      logoUrl: require('../../assets/images/logo.png')
    }
  },
  name: 'layout',
  components: {
    Navbar,
    Sidebar,
    AppMain
  },
  mixins: [ResizeMixin],
  computed: {
    sidebar() {
      return this.$store.state.app.sidebar
    },
    device() {
      return this.$store.state.app.device
    },
    classObj() {
      return {
        hideSidebar: !this.sidebar.opened,
        withoutAnimation: this.sidebar.withoutAnimation,
        mobile: this.device === 'mobile'
      }
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
  @import "src/styles/mixin.scss";
  .app-wrapper {
    @include clearfix;
    position: relative;
    height: 100%;
    width: 100%;
  }

  .jj{
    display: flex;
    flex-direction: column;
  }
  .jj-header {
    width: 100%;
    height: 60px;
    background: #fff;
    border-bottom: 1px solid #e0e4e9;
    box-shadow: 10px 1px 15px rgba(0,0,0,.17);
    position: fixed;
    z-index: 1000;
    display: flex;
    flex-direction:row;
    justify-content: space-between;
  }
  .jj-header-logo {
    width: 231px;
    height: 100%;
    text-align: center;
    font-size: 26px;
    /*margin-top: 14px;*/
    color: lightslategray;
  }
  .jj-header-logo-img{
    width: 220px;
    margin-left: -10px;
    margin-top: -2px;
  }
  .jj-header-right{
    line-height: 60px;
    display: flex;
  }
  .jj-header-user-img , .jj-header-edit-pwd , .jj-header-logout, .jj-header-select-role, .jj-header-message{
    display: flex;
    align-items: center;
    margin-right: 40px;
    cursor: pointer;
  }
  .jj-edit-pwd-icon,.jj-logout-icon{
    width: 18px;
    height: 18px;
    cursor: pointer;
  }
  .jj-user-logo{
    width: 32px;
    height: 32px;
    margin-right: 10px;
  }
</style>
