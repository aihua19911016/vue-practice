<template>
    <div class="login">
        <el-form :model="loginForm" label-width="100px">

            <h1 class="title">
                登录
            </h1>

            <el-form-item label="账号" prop="username">
                <el-input type="password" v-model="loginForm.username" autocomplete="off"></el-input>
            </el-form-item>

            <el-form-item label="密码" prop="password">
                <el-input type="password" v-model="loginForm.password" autocomplete="off"></el-input>
            </el-form-item>


            <el-form-item>
                <el-button type="primary">提交</el-button>
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

                }
            };
        },
        methods: {
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
