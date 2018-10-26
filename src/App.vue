<template>
  <div id="app">
    <div id="nav">
      <div class="container">
        <el-row>
          <el-col :span="12">
            <a class="default" href="">网站首页</a>
            <span>|</span>
            <a class="disabled" href="">欢迎访问瑞金医院舟山分院官方网站</a>
            <a class="default" href="">请登陆</a>
            <span>|</span>
            <a class="default" href="">新用户注册</a>
          </el-col>
          <el-col :span="12" class="right">
            <a class="default" href="">大众版</a>
            <span>|</span>
            <a class="default" href="">专业版</a>
            <span>|</span>
            <a class="default" href="">ENGLISH</a>
          </el-col>
        </el-row>
      </div>
    </div>
    <div id="banner">
      <div class="container">
        <div class="img"></div>
        <div class="searchBar">
          <div class="searchContent">
            <div class="icon el-icon-search"></div>
            <input class="searchInput" type="text" autofocus autocomplete="off" placeholder="输入关键词">
            <a class="searchBtn" href="javascript:;">搜索</a>
          </div>
        </div>
      </div>
    </div>
    <div id="menusBar">
      <div class="container">
        <el-row>
          <el-col :span="24/menuList.length" v-for="(item, index) in menuList" :key="index">
            <a href="javascript:;" :class="index == isActive ? 'active' : ''" v-text="item.name" @click="changeMenus(index)"></a>
          </el-col>
        </el-row>
      </div>
    </div>
    <div id="lunbo">
      <div class="content">
        <div class="item" v-for="(item, index) in lunboList" :key="index" :class="index == itemIsShow ? 'itemShow' : ''">
          <a :href="item.url">
            <img :src="item.imgUrl" :alt="item.title">
          </a>
        </div>
      </div>
      <div class="control"></div>
    </div>
    <div id="quickNavigation">

    </div>
  </div>
</template>

<script>


export default {
  name: 'app',
  components: {
    
  },
  data() {
    return {
      menuList: [
        {name: '首页', uri: '/'},
        {name: '医院概况', uri: '/'},
        {name: '医院动态', uri: '/'},
        {name: '人才招聘', uri: '/'},
        {name: '患者服务', uri: '/'},
        {name: '科室设置', uri: '/'},
        {name: '医师介绍', uri: '/'},
        {name: '科研教育', uri: '/'},
        {name: '护理天地', uri: '/'},
        {name: '党建文化', uri: '/'},
        {name: '院务公开', uri: '/'},
        {name: '专题专栏', uri: '/'},
      ],
      lunboList: [
        {title: "轮播1", url: "javascript:;", imgUrl: 'http://www.zsrjh.com/static/image/slider/banner_01.jpg'},
        {title: "轮播2", url: "javascript:;", imgUrl: 'http://www.zsrjh.com/static/image/slider/banner_02.jpg'},
        {title: "轮播3", url: "javascript:;", imgUrl: 'http://www.zsrjh.com/static/image/slider/banner_03.jpg'},
        {title: "轮播4", url: "javascript:;", imgUrl: 'http://www.zsrjh.com/static/image/slider/banner_04.jpg'},
      ],
      timer: null,
      isActive: 0,
      itemIsShow: 1,
    }
  },
  methods: {
    changeMenus(index) {
      this.isActive = index
    },
    changeLunbo(index) {
      if (index) {
        this.itemIsShow = index
      } else {
        this.itemIsShow == 3 ?  this.itemIsShow = 0 : this.itemIsShow+=1
      }
    },
    play () {
      let self = this;
      this.timer = setInterval(function () {
        self.changeLunbo()
      }, 3000)
    },
    stop () {
      clearInterval(this.timer)
    }
  },
  created () {
    this.play()
  }
}
</script>

<style lang="scss" scoped>
  #nav {
    width: 100%;
    height: 40px;
    line-height: 40px;
    background: #F1F1F1;
    overflow: hidden;
    a {
      padding: 0 5px;
    }
    .container {
      .right {
        display: flex;
        justify-content: flex-end;
      }
    }
  }
  #banner {
    height: 120px;
    width: 100%;
    background: #FFFFFF;
    overflow: hidden;
    .container {
      display: flex;
      justify-content: flex-start;
    }
    .img {
      width: 50%;
      height: 110px;
      background-image: url('../public/logo.png');
      background-repeat: no-repeat;
      margin-top: 10px;
    }
    .searchBar {
      display: flex;
      justify-content: flex-end;
      width: 50%;
      height: 110px;
      align-items: center;
      .searchContent {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        width: 350px;
        height: 40px;
        background: #0872B8;
        .icon {
          margin: 5px 0px 5px 5px;
          height: 30px;
          width: 30px;
          text-align: center;
          line-height: 30px;
          background: #FFF;
        }
        .searchInput {
          margin: 5px 5px 5px 0px;
          width: 250px;
          height: 30px;
          padding: 0;
          padding-left: 5px;
          border: 0;
          outline: none;
        }
        .searchBtn {
          margin: 5px 5px 5px 0px;
          width: 65px;
          color: #FFFFFF;
          line-height: 30px;
          text-align: center;
        }
      }
    }
  }
  #menusBar {
    height: 40px;
    width: 100%;
    overflow: hidden;
    background: rgba(0, 114, 187, 0.9);
    text-align: center;
    line-height: 40px;
    a {
      display: block;
      width: 100%;
      height: 100%;
      transition: 0.5s;
      color: #FFFFFF;
      background: rgba(3, 78, 125, 0);
    }
    a.active {
      background: #034E7D;
    }
  }
  #lunbo {
    position: relative;
    height: 430px;
    width: 100%;
    overflow: hidden;
    .content {
      position: absolute;
      height: 430px;
      width: 100%;
      overflow: hidden;
      .item {
        position: absolute;
        height: 430px;
        opacity: 0;
        transition: 0.5s;
      }
      .item a{
        display: block;
        width: 100%;
        height: 100%;
        overflow: hidden;
      }
      .item.itemShow {
        opacity: 1;
      }
    }
  }
  #quickNavigation {
    height: 130px;
    width: 100%;
    background: linear-gradient(to left, #26A95F 0%,#2A72AB 100%);
  }
  .container {
    width: 1200px;
    overflow: hidden;
    margin: 0 auto;
    *::selection {
      background: none;
    }
    span {
      color: #999999;
    }
  }
  a {
    font-size: 14px;
    text-decoration: none;
    &.disabled {
      color: #999999;
    }
    &.default {
      color: #333333;
      &:hover {
        color: #0872B8
      }
    }
  }
</style>
