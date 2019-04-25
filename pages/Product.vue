<template>
  <div id="product">
    <el-carousel :interval="5000" :loop="true" height="450px">
      <el-carousel-item v-for="(item,i) in carouselList" :key="i">
        <img :src="item.src" alt="" style="margin-left:-400px">
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
import axios from "axios";
export default {
  async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
    let {data}=await axios.get('http://127.0.0.1:3001/index/product');
    return {carouselList:data}
  },
  data(){
    return {
      title:'小华科技有限公司-产品介绍'
    }
  },
  head(){
    return {
      title:this.title,
      meta:[
        {hid:'description',name:'description',content:'小华科技有限公司,产品介绍,移动客户端,管理网关,智能控制,电动窗帘,家庭娱乐,影音多媒体,看护摄像机,视频监控,背景音乐'}
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
