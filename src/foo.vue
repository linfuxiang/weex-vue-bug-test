<template>
  <div class="wrapper">
    <!-- <div class="top" @click="update" ref="top">
      <text>顶部导航栏</text>
    </div>
    :style="{height:hei}"
    <list>
      <cell v-for="item in items">
        <image src="https://alibaba.github.io/weex/img/weex_logo_blue@3x.png" class="logo"></image>
        <text class="title">Hello {{item}}</text>
      </cell>
    </list>
    <div class="inp" ref="inp">
      <input type="text" class="input" v-model="inputVal"></input>
    </div>
    <div class="aaaa" ref="aaaa"></div> -->
    <div v-html="abc" class="aaa"></div>
  </div>
</template>

<style>
.aaa {
  font-size: 30px;
  color: red;
  }
  .wrapper {
    flex-direction: column;
    justify-content: space-between;
    align-items: stretch;
    height: 100%;
  }
  .top {
    /*position: fixed;*/
    top: 0;
    z-index: 10;
    height: 100px;
    width: 750px;
    background-color: red;
  }
  .pad {
    /*height: 100px;*/
  }
  .wrapper { 
    align-items: center;
    /*margin-top: 100px;*/
    /*padding-bottom: 100px;*/
    width: 750px;
    /*height: 800px;*/
  }
  .title { 
    font-size: 48px; 
  }
  .logo { 
    width: 360px; 
    height: 82px; 
  }
  .inp {
    /*position: fixed;*/
    /*bottom: 1000px;*/
    height: 100px;
    width: 750px;
    background-color: yellow;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
  }
  .inputt {

  }
  .input {
    /*position: absolute;*/
    /*bottom: 0px;*/
    width: 500px;
    height: 50px;
    background-color: #f0ede2;
  }
  .aaaa {
    position: fixed;
    bottom: 0px;
    width: 750px;
    height: 0px;
  }
</style>

<script>
  const dom = weex.requireModule('dom')

  export default {
    data() {
      return {
        logoUrl: 'https://alibaba.github.io/weex/img/weex_logo_blue@3x.png',
        target: 'World',
        items: [1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4],
        inputVal: '',
        hei: '800px',
        abc: '<text class="aaa">123</text><a href="https://baidu.com"><text class="aaa">abc</text></a>'
      }
    },
    methods: {
      update: function (e) {
        dom.getComponentRect(this.$refs.aaaa, option => {
          this.hei = option.size.top - 200 + 'px';
          console.log(this.hei)
          console.log('getComponentRect:', option.size)
        })
        dom.getComponentRect(this.$refs.top, option => {
          // this.hei = option.size.top - 
          console.log('getComponentRect:', option.size)
        })
      }
    },
    mounted() {
      console.log(weex.config)
      dom.getComponentRect(this.$refs.inp, option => {
        console.log('getComponentRect:', option.size)
      })
      dom.getComponentRect(this.$refs.aaaa, option => {
        console.log('getComponentRect:', option.size)
      })
    },
  }
</script>
