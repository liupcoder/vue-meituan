<template>
  <div class="page-register">
    <article class="header">
      <header>
        <a href="/" class="site-logo" />
        <span class="login">
          <em class="bold">已有美团账号</em>
          <a href="/login">
            <el-button type="primary" size="small">登录</el-button>
          </a>
        </span>
      </header>
    </article>
    <section>
      <el-form ref="ruleForm" :model="ruleForm" label-width="80px">

        <el-form-item label="昵称">
          <el-input v-model="ruleForm.name" prop="name"></el-input>
        </el-form-item>
        <el-form-item label="邮箱">
          <el-input v-model="ruleForm.email" prop="email"></el-input>
          <el-button size="mini" round @click="sendMsg">发送验证码</el-button>
          <span class="status">{{ statusMsg }}</span>
        </el-form-item>

        <el-form-item label="验证码">
          <el-input
            v-model="ruleForm.code"
            prop="code"
            maxlength="4"
          ></el-input>
        </el-form-item>

        <el-form-item label="密码">
          <el-input
            type="password"
            v-model="ruleForm.pwd"
            prop="pwd"
          ></el-input>
        </el-form-item>

        <el-form-item label="确认密码">
          <el-input
            type="password"
            v-model="ruleForm.cpwd"
            prop="cpwd"
          ></el-input>
        </el-form-item>

        <el-form-item>
          <el-button type="primary" @click="register">
            同意以下协议并注册
          </el-button>
          <div class="error">{{ error }}</div>
        </el-form-item>
        <el-form-item>
          <a
            class="f1"
            href="https://rules-center.meituan.com/rules-detail/4"
            target="_blank"
            >《美团点评用户服务协议》</a
          >
        </el-form-item>
      </el-form>
    </section>
  </div>
</template>

<script>
export default {
  layout: "blank",
  data() {
    return {
      statusMsg: "",
      error: "",
      ruleForm: {
        name: "",
        code: "",
        pwd: "",
        cpwd: "",
        email: ""
      },
      rules: {
        name: [
          {
            required: true,
            type: "string",
            messge: "请输入昵称",
            trigger: "blur"
          }
        ],
        email: [
          {
            required: true,
            type: "email",
            messge: "请输入邮箱",
            trigger: "blur"
          }
        ],
        pwd: [
          {
            required: true,
            messge: "创建密码",
            trigger: "blur"
          }
        ],
        cpwd: [
          {
            required: true,
            messge: "确认密码",
            trigger: "blur"
          },
          {
            validator: (rule, value, callback) => {
              if (value === "") {
                callback();
              }
            }
          }
        ]
      }
    };
  },
  methods: {
    sendMsg: function() {},
    register: function() {}
  },
  components: {}
};
</script>

<style lang="scss">
@import "@/assets/css/register/index.scss";
</style>
