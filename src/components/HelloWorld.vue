<template>
  <el-container id="container">
    <el-header height="80px" >
      <div id="top-bookmark">
         <el-button class="el-icon-s-home"> 首页 </el-button>
        <el-tooltip v-for="(item,key) in awaysuse" :key="key" class="item" effect="dark" :content="item.descript" placement="bottom" >
          <el-button><el-link :underline="false" target="_blank" :href="item.url"> {{ item.name }} </el-link></el-button>
        </el-tooltip>
      </div>
    </el-header>
    <el-divider></el-divider>
    <el-container id="center-container">
      <el-aside width="300px">
         <el-card :body-style="{ padding: '0px' }">
          <img src="https://shadow.elemecdn.com/app/element/hamburger.9cf7b091-55e9-11e9-a976-7f4d0b07eef6.png" class="image">
          <el-menu
          default-active="1"
          class="el-menu-vertical-demo"
          background-color="#F56C6C"
          text-color="#fff"
          @select="changeMenu"
          active-text-color="6B97FF">
          <el-menu-item v-for="(item,index,key) in bookmarks" :key="key" :index="(index).toString()">
            <i class="el-icon-collection-tag"></i>
            <span slot="title"> {{ item.typename }} </span>
          </el-menu-item>
          </el-menu>
        </el-card>
      </el-aside>
      <el-container id="content-container">
        <el-carousel id="banner" :interval="4000" type="card" height="200px">
          <el-carousel-item v-for="(item,key) in banners" :key="key">
            <el-image :src="item.url"></el-image>
          </el-carousel-item>
        </el-carousel>
        <div id="bookmarks">
            <div style="min-width:10px;margin:0 auto;" v-if='bookmarks.length>0'>
         
              <el-card class="box-card" v-for="(item,key) in bookmarks[keyindex].datas" :key="key">
                <el-link :underline="false" target="_blank" :href="item.url"><el-avatar :size="50" :src="item.img"></el-avatar></el-link>
                <p> {{ item.name }}</p>
              </el-card>
            </div>
        </div>
      </el-container>
    </el-container>
    <el-divider></el-divider>
    <el-footer><span>@ 2019 水寒 浙ICP备18045315号-1</span></el-footer>
  </el-container>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      banners:[],
      awaysuse: [],
      bookmarks: [],
      keyindex:0,
    }
  },
  created(){
    axios.get('http://qiniucdn.dp2px.com/test.json').then(response => {
      this.banners = response.data
    });
    axios.get('http://qiniucdn.dp2px.com/bookmark.json').then(response => {
      this.bookmarks = response.data
    });
    axios.get('http://qiniucdn.dp2px.com/aways-use.json').then(response => {
      this.awaysuse = response.data
    });
  },
  methods: {
    changeMenu(key, i){
      console.log(key)
      this.keyindex = key;
      //this.showbookmark = this.bookmarks[key].datas
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  #container{
    width: 100%;
    flex-direction: column;
    height: 100%;
    display: flex;
    overflow-x:hidden;
    overflow-y:scroll;
  
  }
  .el-divider{
    margin:0;
  }
  .el-header{
    background: #409EFF;
    line-height: 80px;
    text-align: center;
  }
  .el-main{
    font-size:100px;
  }

  .el-footer{
    font-size: 14px;
    line-height: 60px;
    text-align: center;
    background: #606266;
    color: white;
  }
  #center-container{
     background: white;
     flex: 1;
  }

  .el-card,.box-card{
     width:200px; 
     display: inline-block;
     margin: 20px;
  }

  .box-card p{
    margin: 5px;
  }

  #top-bookmark{
     height: 80px;
  }

  #content-container{
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    overflow-x:hidden;
  }

  .el-aside{
    background: #b3d8ff;
  }

  #banner{
    width: 70%;
    margin: 20px auto 0;
  }

  #bookmark>>>.el-carousel__container{
    height:100%;
  }

  .el-carousel__item h3 {
    color: #475669;
    font-size: 14px;
    opacity: 0.75;
    line-height: 200px;
    margin: 0;
  }
  
  .el-carousel__item:nth-child(2n) {
    background-color: #99a9bf;
  }
  
  .el-carousel__item:nth-child(2n+1) {
    background-color: #d3dce6;
  }

  #bookmarks{
    margin: 20px;
  }
  .el-row {
    margin: 20px;
  }
  .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 120px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
</style>