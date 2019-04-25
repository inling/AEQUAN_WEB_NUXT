<template>
  <div id="app">
    <el-container>
      <el-header class="header">
        <el-row class="logo-row">
          <el-col :span="24">
            <router-link to="/">
              <img src="../assets/img/logo.jpg" alt="">
            </router-link>
          </el-col>
        </el-row>
        <el-row>
          <el-col :span="24">
            <div class="grid-content bg-purple-dark">
              <el-row class="nav">
                <el-col v-for="(item,i) in navList" :key="i" :span="3">
                  <router-link :to="item.router" v-text="item.tag"  :class="{'nav_active':item.navActive}"></router-link>
                </el-col>
              </el-row>
            </div>
          </el-col>
        </el-row>
      </el-header>
      <el-main  class="main">
        <nuxt />
      </el-main>
      <el-footer  class="footer">
        <el-card class="box-card">
          <div v-for="(item,i) in infoList" :key="i" class="text" v-html="item.text"></div>
        </el-card>
        <div class="qycode">

        </div>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
export default {
    data(){
    return {
      navList:[
        {tag:'公司介绍',router:'/',navActive:false},
        {tag:'系统介绍',router:'/system',navActive:false},
        {tag:'解决方案',router:'/solution',navActive:false},
        {tag:'产品介绍',router:'/product',navActive:false},
        {tag:'应用领域',router:'/area',navActive:false},
        {tag:'项目案例',router:'/case',navActive:false},
        {tag:'安e商城',router:''},
      ],
      infoList:[
        {text:'©2014大华股份 DESIGNED BY: 小华科技 '},
        {text:'集团链接： <a href="https://www.dahuatech.com/">大华股份</a>'},
        {text:'公司地址：浙江省杭州市滨江区滨安路1187号'},
        {text:'电话：+86-571-28983132    +86-571-28991065'},
      ]
    }
  },
  created(){
    this.justifyRoute(this.$route.path)
  },
  mounted(){
    var ane=document.querySelector('.nav .el-col:last-child a');
    ane.onclick=function(){
      window.location.href="http://60.12.11.59:8084/"
      return false;
    }
  },
  methods:{
    justifyRoute(route_path){
      for(let i=0;i<this.navList.length;i++){
        this.navList[i].navActive=false;
        if(route_path==this.navList[i].router){
          this.navList[i].navActive=true;
        }
      }
    }
  },
  watch:{
    $route(to){
      this.justifyRoute(to.path)
    }
  }
}
</script>

<style lang="scss">
  .el-carousel{
    border-bottom: 1px solid #d4d4d4;
    box-shadow: 0px 1px 48px #d4d4d4;
    .el-carousel__indicators{
      right:80px;
      left:unset;
      .el-carousel__indicator{
        .el-carousel__button{
          width:10px;
          height:10px;
          background:#86878D;
          border-radius:50%;
        }
        &:hover button{
          transition: .2s linear;
          transform: scale(1.2)
        }
      }
      .el-carousel__indicator.is-active button{
        background:red;
        transition: .2s linear;
        transform: scale(1.2)
      }
    }
  }

  .header,.main,.footer{
    padding:0 !important;
  }
  .header{
    text-align: center;
    height:100% !important;
    .logo-row{
      width:980px;
      margin:0 auto;
      text-align:left;
      .el-col{
        margin-top:8px;
      }
    }
    .nav{
      width:980px;
      height:100%;
      line-height: 35px;
      margin:0 auto;
      .el-col{
        cursor: pointer;
        a{
          display: inline-block;
          width:100%;
          height:100%;
          color:white;
          font-size: 14px;
          &:hover{
            background:#616369;
          }
        }
      }
    }
  }

  .nav_active{
    background:#D9070A !important;
  }

  .footer{
    position:fixed;
    bottom: 0;
    left:0;
    z-index:1000;
    height:117px !important;
    width:100%;
    background-color: #7D7F84 !important;
    .box-card{
      margin:auto 0;
      border:1px solid #7D7F84;
      border-radius:0;
      height:100%;
      
      .el-card__body {
        padding: 10px 10px 10px 150px;
        background-color: #7D7F84 !important;
      }
      .text {
        font: normal 12px/24px "Microsoft YaHei";
        color:white;
      }
      a{
        text-decoration: underline;
        color:white;
        &:hover{
          color:#d1d3d8;
        }
      }
    }
    
    .qycode{
      position: absolute;
      height:200px;
      width:200px;
      top:10px;
      right:150px;
      background: url(../assets/img/foot_er.jpg) no-repeat right 0;
    }
  }
</style>
