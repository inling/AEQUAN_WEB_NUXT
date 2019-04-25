<template>
    <div class="home">
    <el-carousel :interval="5000" :loop="true" height="450px">
      <el-carousel-item v-for="(item,i) in carouselList" :key="i">
        <img :src="item.src" alt="" style="margin-left:-400px">
      </el-carousel-item>
    </el-carousel>
  </div>
  <!--
  <section class="container">
    <div>
      <logo />
      <h1 class="title">
        aequan_web_nuxt
      </h1>
      <h2 class="subtitle">
        My cool Nuxt.js project
      </h2>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >Documentation</a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >GitHub</a>
      </div>
    </div>
  </section>
  -->
</template>

<script>
/*
import Logo from '~/components/Logo.vue'

export default {
  components: {
    Logo
  }
}*/
import axios from 'axios';

export default {
  name: 'home',
  async asyncData({isDev, route, store, env, params, query, req, res, redirect, error}) {
    let {data}= await axios.get('http://127.0.0.1:3001/index');
    return {carouselList:data}
  },
  data(){
    return {
      title:'小华科技有限公司'
    }
  },
  head(){
    return {
      title:this.title,
      meta:[
        {hid:"description",name:"description",content:"小华科技有限公司,公司介绍"}
      ]
    }
  },
  transition:{
    name:'test',
  },
  created(){
    
  },
  mounted(){
    
  },
  methods:{

  }
}

</script>

<style>
/*
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}*/

</style>
