<template>
    <div class="login">
        <el-form :model="loginForm" :rules="loginRules" ref="loginForm" label-width="100px">

            <h1 class="title">
                登录
            </h1>

            <el-form-item label="账号" prop="username">
                <el-input type="text" v-model="loginForm.username" autocomplete="off"></el-input>
            </el-form-item>

            <el-form-item label="密码" prop="password">
                <el-input type="password" v-model="loginForm.password" autocomplete="off"></el-input>
            </el-form-item>


            <el-form-item>
                <el-button type="primary" @click="login()">登录</el-button>
            </el-form-item>
        </el-form>

    </div>
</template>
<script>
    import ElButton from "../../node_modules/element-ui/packages/button/src/button.vue";

    export default {
        components: {ElButton},
        data() {
            return {
                //登录表单的数据
                loginForm: {
                    username: '',
                    password: ''

                },
                //验证规则
                loginRules: {
                    username: [
                        {require: true, message: '请输入用户名', trigger: 'blur'},
                        {min: 5, max: 18, message: '长度在5到18个字符之间', trigger: 'blur'}
                    ],
                    password: [
                        {require: true, message: '请输入密码', trigger: 'blur'},
                        {min: 5, max: 18, message: '长度在5到18个字符之间', trigger: 'blur'}
                    ]
                }
            };
        },
        methods: {
            login() {//登录
                this.$refs.loginForm.validate(valid => {//表单验证
                    if (valid) {
                        //保留this
                        let _this = this;
                        this.axios.post('/api/checklogin', {
                            username: this.loginForm.username,
                            password: this.loginForm.password

                        })
                            .then((response) => {
                                console.log('接收后端响应登录的请求数据')
                            });

                        console.log(this.axios)
                    } else {
                        console.log('login err');
                        return false;
                    }
                })
            }
        }


    }

</script>
<style>
    html, body {
        margin: 0;
        padding: 0;
    }

    html, body, #app, .login {
        height: 100%;
    }

    .login {
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .el-form {
        width: 400px;
        border: 1px solid #ccc;
        border-radius: 40px;
        padding: 0 45px 10px 10px;
    }

    .el-form .title {
        font-size: 22px;
        color: #333;
        font-weight: bold;
        padding: 20px 0 20px 60px;
    }

</style>
