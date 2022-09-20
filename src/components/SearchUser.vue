<template>
    <section class="jumbotron">
        <h3 class="jumbotron-heading">Search Github Users</h3>
        <div>
          <input type="text" placeholder="enter the name you search" v-model="KeyWord"/>&nbsp;
          <button @click="searchUsers">Search</button>
        </div>
      </section>
</template>

<script>
    import axios from 'axios'

export default {
    name:'SearchUser',
    data(){
        return{
            KeyWord:''
        }
    },
    methods:{
        searchUsers(){
            //请求前更新List的数据
            this.$bus.$emit('updataListData',{isFirst:false,isLoading:true,errMsg:'',users:[]}),
            axios.get(`https://api.github.com/search/users?q=${this.KeyWord}`).then(
                response =>{
                    //请求成功后更新List的数据
                    this.$bus.$emit('updataListData',{isLoading:false,errMsg:'',users:response.data.items})
                },
                error=>{
                    //请求失败后更新List的数据
                    console.log('请求失败了',error.message);
                    this.$bus.$emit('updataListData',{isLoading:false,errMsg:error.message,users:[]})

                }
            )
        }
    }

} 
</script>   