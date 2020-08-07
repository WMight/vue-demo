<template>
    <div>
        <div class="name">{{loginName}}</div>
        <div class="welcome">欢迎来到个人中心</div>
        <button @click="toAdd()">添加</button>
    </div>
</template>

<script>
export default {
    data () {
        return {
            loginName :localStorage.getItem("name")
        }
    },
    methods:{
        toAdd(){
            this.$router.push('/add')
        }
    }
}
</script>

<style lang="scss" scoped>
div{
    text-align: center;
    margin: 20px 0;
}
</style>