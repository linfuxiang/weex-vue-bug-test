<template>
  <div>
    <div class="top">
      <text>顶部导航栏</text>
    </div>
    <list class="wrapper">
      <cell v-for="item in items">
        <image src="https://alibaba.github.io/weex/img/weex_logo_blue@3x.png" class="logo"></image>
        <text class="title">Hello {{item}}</text>
      </cell>
    </list>
    <div class="inp">
      <input type="text" class="input" v-model="inputVal"></input>
    </div>
  </div>
</template>

<style>
  .top {
    position: fixed;
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
    margin-top: 100px;
    /*padding-bottom: 100px;*/
    width: 750px;
    height: 834px;
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
    /*bottom: 0px;*/
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
</style>

<script>
  export default {
    data() {
      return {
        logoUrl: 'https://alibaba.github.io/weex/img/weex_logo_blue@3x.png',
        target: 'World',
        items: [1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4,1,2,3,4],
        inputVal: ''
      }
    },
    methods: {
      update: function (e) {
        this.target = 'Weex'
        console.log('target:', this.target)
      }
    }
  }
</script>
