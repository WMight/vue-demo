<template>
    <div>
        <p>标题</p>
        <input type="text" v-model="title">
        <p>内容</p>
        <input type="text" v-model="content">
        <div class="btn" @click="add()">添加</div>
    </div>
</template>

 <script>
import store from '../store/index.js'
export default {
    name: "add",
    data () {
        return {
            title: '',
            content: ''
        }
    },
    methods: {
        add () {
            if(this.title !== '' && this.content !== ''){
                store.commit('addItem',{
                title: this.title,
                content: this.content
                })
                this.title = ''
                this.content = ''
                this.$router.push('/home/list')
            }else{
                alert('请输入内容');
            }
        }
    }
}
 </script>

 <<style lang="scss" scoped>
 .btn{
     margin-top:40px;
     width: 140px;
     height: 40px;
     line-height: 40px;
     text-align: center;
     border:1px solid #42b983;
     border-radius: 30px;
     background-color:#42b983;
     cursor:pointer;
 }
 </style>