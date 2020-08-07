<template>
    <div>
        <form action="" v-if="!isReg">
        <h2 class="title">欢迎登录</h2>
        
            <div class="name">用户名：</div>
            <input type="text" v-model="name">
            <br>
            <div class="password">密码：</div>
            <input type="password" v-model="password">
            <div class="btn">
                <button type="button" @click="login()">登录</button>
                <button type="button" @click="reg()">注册</button>
            </div>
            
        </form>
        <form action="" v-else>
            <h2 class="title">请输入以下信息</h2>
            <div class="name">用户名：</div>
            <input type="text" v-model="name">
            <div class="password">密码：</div>
            <input type="password" v-model="password">
            <div class="password">再次输入密码：</div>
            <input type="password" v-model="repeat">
            <button type="button" @click="addUser()">确定</button>
            <button type="button" @click="cancel()">取消</button>
        </form>
    </div>
</template>

<script>
export default {
    name: "Login",
    data () {
        return {
            isReg: false,
            name: '',
            password: '',
            repeat: ''
        }
    },
    methods: {
        login () {
            if(localStorage.getItem("name") === this.name && localStorage.getItem("password") === this.password && this.name !== '' && this.password !== ''){
                this.name = ''
                this.password = ''
                this.$router.push('/home/list')
            }else{
                alert('用户名密码不正确')
            }
        },
        reg () {
            this.isReg = true
        },
        addUser () {
            if(this.password === this.repeat){
                localStorage.setItem("name", this.name)
                localStorage.setItem("password", this.password)
                this.name = ''
                this.password = ''
                this.isReg = false
            }else{
                alert('两次输入密码不一致')
            }
            
        },
        cancel () {
            this.isReg = false
        }
    }
}
</script>

<style lang="scss" scoped>
.title{
    margin: 20px 20px;
}
.name,.password{
    margin: 30px 20px;
    display: inline-block;
    width: 130px;
}
button{
    width: 140px;
    height: 50px;
    margin: 2px 29px;
    border-radius: 20px;
    border-style: none;
    background-color: #42b983;
    color: #fff;
}
</style>