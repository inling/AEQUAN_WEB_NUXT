<template>
  <div id="solution">
    <el-carousel :interval="5000" :loop="true" height="450px">
      <el-carousel-item v-for="(item,i) in carouselList" :key="i">
        <img :src="item.src" alt="" style="margin-left:-400px">
      </el-carousel-item>
    </el-carousel>
  </div>
</template>

<script>
export default {
  data(){
    return {
      carouselList:[]
    }
  },
  created(){

  },
  mounted(){
    this.getCList();
  },
  methods:{
    getCList(){
      var self=this;
      this.$axios.get('http://127.0.0.1:3001/index/solution').then(res=>{
        self.carouselList=res.data;
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.el-carousel{
  border-bottom: 1px solid #d4d4d4;
  box-shadow: 0px 1px 48px #d4d4d4;
}
</style>
