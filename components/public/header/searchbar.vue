<template>
  <div class="search-panel">
    <el-row class="m-header-searchbar">
      <el-col
        :span="3"
        class="left"
      >
        <img src="//s0.meituan.net/bs/fe-web-meituan/e5eeaef/img/logo.png">
      </el-col>
      <el-col
        :span="15"
        class="center"
      >
        <div class="wrapper">
          <el-input
            v-model="search"
            placeholder="搜索商家或地点"
            @focus="searchFocus"
            @blur="searchBlur"
            @input="searchInput"/>
          <el-button
            slot="append"
            icon="el-icon-search"
          />
          <el-col>
            <dl
              v-if="isfocus"
              :span="12"
              class="hotPlace"
            >
              <dt>热门搜索</dt>
              <dd><a href="#">故宫博物院</a></dd>
              <dd><a href="#">故宫博物院</a></dd>
              <dd><a href="#">故宫博物院</a></dd>
              <dd><a href="#">故宫博物院</a></dd>
            </dl>
          </el-col>
          <el-col
            v-if="isComputedSearching"
            :span="12"
          >
            <dl class="searchList">
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
              <dd><a href="#">天坛</a></dd>
            </dl>
          </el-col>
        </div>
        <p class="suggest">
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
          <a href="#">故宫博物院</a>
        </p>
        <ul class="nav">
          <li><nuxt-link
            to="/"
            class="takeout">美团外卖</nuxt-link></li>
          <li><nuxt-link
            to="/"
            class="movie">猫眼电影</nuxt-link></li>
          <li><nuxt-link
            to="/"
            class="hotel">美团酒店</nuxt-link></li>
          <li><nuxt-link
            to="/"
            class="apartment">民宿/公寓</nuxt-link></li>
          <li><nuxt-link
            to="/"
            class="business">商家入驻</nuxt-link></li>
        </ul>
      </el-col>
      <el-col
        :span="6"
        class="right"/>
    </el-row>
  </div>
</template>
<script>
export default {
  data() {
    return {
      search:'',
      isfocus: false,
      isSearching: false
    }
  },
  computed:{
    isComputedSearching:function(){
      return this.isSearching && this.search
    }
  },
  methods: {
    searchFocus:function() {
      this.isfocus = true
    },
    searchBlur:function() {
      //设置延时，否则点击热点时会自动隐藏掉
      setTimeout(()=> {
        this.isfocus = this.isSearching = false
      },200)
    },
    searchInput(){
      this.isSearching = true
    }
  }
}

</script>
<style lang="scss">
.downlist {
  display: flex
}

</style>
