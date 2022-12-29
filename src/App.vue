<template>
  <!-- 0.v-bind -->
  <div class="page">
    <div class="bg-video">
      <video src="https://s3plus.meituan.net/zhaopin-official-website-prod/video/campusTV/zippedHomeVideo.mp4" autoplay
        loop></video>
    </div>
    <div class="container">

      <div></div>
      <!-- 页面描述部分-->
      <div class="desc">
        <div class="header_bg" style="cursor: pointer;" >
          <h1 class="logo">王吉祥的站</h1>
        </div>

      </div>
      
      
      
      <div class="login">
        <div class="tab_title">QQ账号登录</div>
        <div class="login-all">
          <div class="login-wrapper">
            <child-comp v-if="isShowChild"></child-comp>

          <div class="login_tips" style="box-sizing: content-box padding-bottom: 8px">
            <div class="tips_note">登陆后高清播放更流畅</div>
          </div>

          <div class="tips">
            <div class="title2">密码登录</div>
            <div class="title3">推荐使用快捷登录，防止盗号</div>
          </div>
          
          <el-form :model="form" label-width="80px">
            <el-form-item label="用户名：">
              <el-input v-model="form.name"></el-input>
            </el-form-item>
            <el-form-item label="密码：">
              <el-input v-model="form.passwd" show-password></el-input>
            </el-form-item>
          </el-form>
          <div class="operator">
            <el-button size="small" @click="login">登录</el-button>
          </div>
        </div>
      </div>
    </div>
        </div>
        
  </div>
</template>

<script>
import ChildComp from './components/ChildComp.vue';
export default {
  // components
  components: {
    ChildComp,
  },

  // 预定义属性
  name: 'App',
  // 组件当中所有的响应式数据
  data: function () {
    return {
      form: {
        name: '',
        passwd: ''
      },
      isShowChild: true,
    }
  },
  // 方法
  methods: {
    createHelloMsg() {
      console.log(this.info)
    },
    checkParams() {
      return this.form.name && this.form.passwd;
    },
    login() {
      // 参数校验
      if (!this.checkParams()) {
        this.$notify({
          title: '错误',
          message: '登录参数不完整',
          type: 'error'
        });
      } else {
        // TODO: 网络请求
        // const res = axios.get('url');
        this.$notify({
          title: '成功',
          message: `登录成功, 用户名：${this.form.name}；密码：${this.form.passwd}`,
          type: 'success'
        });
      }
    },
  },

  // 生命周期函数之一
  mounted() {
    // 当 当前组件 被挂载时，出发执行
    setTimeout(() => {
      this.isShow = false,
        this.isHighLight = true
    }, 3000)

    setInterval(() => {
      this.isShowChild = !this.isShowChild;
    }, 3000)
  },
}
</script>


<style lang="scss">
/**
使用了scoped关键字，当前样式只应用于此组件以及子组件，不会影响父组件
*/
html,
body {
  margin: 0;
  padding: 0;
}

.container {
  display: flex;
}

.operator {
  display: flex;
  justify-content: center;
}

.desc {
  width: 60%;
}


.tips_note{
  margin: 5px -10px 5px;
    font-size: 24px;
    line-height: 30px;
    color: #2a2a2a;
    text-align: center;
    zoom: 1;
}

.tab_title{
  
    height: 50px;
    margin-bottom: -1px;
    border-bottom: 1px solid #e6e6e6;
    background: #f1f1f1;
    z-index: 3;
    
    display: flex;
    justify-content: center;
    align-items: center;
}

.login_tips{
  
  position: relative;
    z-index: 3;
    height: 58px;
    padding: 12px 10px;
    background-color: #fff;
}

.tips{
  margin-bottom: 26px;
}



.title2{
  font-size: 20px;
    line-height: 28px;
    
    color: #000;
    margin: 8px 0 6px;
    text-align: center;
}

.title3{
  font-size: 12px;
    line-height: 16px;
    color: #000;
    text-align: center;
}

.login {
  padding-top: 120px;

  .login-wrapper {
    background-color: #fff;
    
    width: 300px;
    padding: 40px;
    padding-top: 0px;
    margin: 0px;
    //border-radius: 10px;
  }
}

.header_bg{
  width: 243px;
  height: 40px;
  font-weight: 400;
  padding-left: 40px;
  background-size: cover;
  display: inline-block;
}
.logo{
  margin: 0px;
  display: flex;
  background: -webkit-linear-gradient(315deg,#42d392 25%,#647eff);
    background-clip: text;
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;

}

.bg-video {
  position: absolute;
  top: 0;
  left: 0;
  z-index: -1;

  video {
    width: 100%;
  }
}


</style>
