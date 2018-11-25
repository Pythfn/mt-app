<template>
  <div class="page-register">
    <article class="header">
      <header>
        <a
          href="/"
          class="site-logo" />
        <span class="login">
          <em class="bold">已有美团账号？</em>
          <a href="/login">
            <el-button
              type="primary"
              size="small">登录</el-button>
          </a>
        </span>
      </header>
    </article>
    <section>
      <el-form
        ref="ruleForm"
        :model="ruleForm"
        :rules="rules"
        label-width="100px"
        class="demo-ruleForm"
      >
        <el-form-item
          label="用户名"
          prop="name"
        >
          <el-input v-model="ruleForm.name" />
        </el-form-item>
        <el-form-item
          label="邮箱"
          prop="email"
        >
          <el-input v-model="ruleForm.email" />
          <el-button
            type="primary"
            size="mini"
            round>发送验证码</el-button>
          <span>{{ codeMsg }}</span>
        </el-form-item>
        <el-form-item
          label="验证码"
          prop="code"
        >
          <el-input
            v-model="ruleForm.code"
            maxlength="4" />
        </el-form-item>
        <el-form-item
          label="密码"
          prop="pass"
        >
          <el-input            
            v-model="ruleForm.pass"
            type="password" />
        </el-form-item>
        <el-form-item
          label="确认密码"
          prop="cpass"
        >
          <el-input
            v-model="ruleForm.cpass"
            type="password"/>
        </el-form-item>
        <el-form-item>
          <el-button
            type="primary"
            @click="onSubmit"
          >同意以下协议并注册</el-button>
        </el-form-item>
        <el-form-item>
          <a
            class="f1"
            href="http://www.meituan.com/about/terms"
            target="_blank">《美团网用户协议》</a>
        </el-form-item>
      </el-form>
      
    </section>

  </div>
</template>
<script>
export default {
  layout: 'blank',
  data() {
    return {
      codeMsg:'',
      ruleForm: {
        name: '',
        email: '',
        code: '',
        pass: '',
        cpass: ''
      },
      rules:{
        name:[{
          required: true,
          type: 'string',
          message: '请输入用户名',
          trigger: 'blur'
        }],
        email:[{
          required: true,
          type: 'email',
          message: '请输入正确的邮箱',
          trigger: 'blur'
        }],
        pass:[{
          required: true,
          message: '请输入正确的密码',
          trigger: 'blur',
        }],
        cpass:[{
          required: true,
          message: '密码不能为空',
          trigger: 'blur',
        },{
        validator: (rule, value, callback) => {
          if(value == '') {
            callback(new Error('密码不能为空'))
          } else if (value !== this.ruleForm.pass){
            callback(new Error('两次密码不一致'))
          } else {
            callback()
          }
        }}]
      }
    }
  }
}

</script>
<style lang="scss">
@import "@/assets/css/register/index.scss";

</style>
