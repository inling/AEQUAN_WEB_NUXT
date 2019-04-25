<template>
  <div id="area">
    <el-carousel :interval="5000" :loop="true" height="450px">
      <el-carousel-item v-for="(item,i) in carouselList" :key="i">
        <img :src="item.src" alt="" style="margin-left:-400px">
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
    let {data}=await axios.get('http://127.0.0.1:3001/index/area');
    return {carouselList:data}
  }, 
  data(){
    return {
      title:'小华科技有限公司-应用领域'
    }
  },
  head(){
    return {
      title:this.title,
      meta:[
        {hid:'description',name:'description',content:'小华科技有限公司,应用领域,智慧大楼应用,智慧社区应用,智慧家庭应用,智慧酒店应用'}
      ]
    }
  },
  transition:{
    name:"test"
  },
  created(){
    
  },
  mounted(){

  },
  methods:{
   
  }

}
</script>

<style lang="scss" scoped>
  .el-carousel{
    border-bottom: 1px solid #d4d4d4;
    box-shadow: 0px 1px 48px #d4d4d4;
  }
</style>


