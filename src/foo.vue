<template>
  <div class="wrapper" append="tree">
    <div class="top" @click="update" ref="top">
      <text>顶部导航栏</text>
    </div>
    <!-- :style="{height:hei}" -->
    <list class="list" @loadmore="onload">
      <!-- <refresh :display="isRefreshing">
        <text>refreshing...</text>
      </refresh> -->
      <cell v-for="item in items" :ref="'item'">
        <image src="https://alibaba.github.io/weex/img/weex_logo_blue@3x.png" class="logo"></image>
        <text class="title">Hello {{item}}</text>
      </cell>
      <cell v-if="isLoading == 'show'">
        <text>loading...</text>
      </cell>
      <!-- <loading :display="isLoading">
        <loading-indicator></loading-indicator>
        <text>loading...</text>
      </loading> -->
    </list>
    <div class="inp" ref="inp">
      <input type="text" class="input" v-model="inputVal"></input>
    </div>
  </div>
</template>

<style>
  .wrapper {
    /*flex-direction: column;*/
    /*justify-content: space-between;*/
    /*align-items: stretch;*/
    /*height: 1000px;*/
    width: 750px;
  }
  .top {
    position: sticky;
    z-index: 10;
    height: 100px;
    width: 750px;
    background-color: red;
  }
  .title { 
    font-size: 48px; 
  }
  .logo { 
    width: 360px; 
    height: 82px; 
  }
  .list {
    height: 1000px;
  }
  .inp {
    height: 100px;
    width: 750px;
    background-color: yellow;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
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
  const dom = weex.requireModule('dom')

  export default {
    data() {
      return {
        logoUrl: 'https://alibaba.github.io/weex/img/weex_logo_blue@3x.png',
        target: 'World',
        items: [1,2,3,4,5,6,7,8,9],
        inputVal: '',
        hei: '800px',
        isLoading: 'hide',
        isRefreshing: 'hide',
      }
    },
    methods: {
      update: function(e) {

        // const el = this.$refs.item5[0]
        // dom.scrollToElement(el, { offset: 0 })
        // dom.getComponentRect(this.$refs.item5, option => {
          // console.log(this.$refs.item5, option)
        // })
        console.log(this.$refs.item, this.$refs.inp)
      },
      onload: function() {
        this.isShowLoading = 'show';
        setTimeout(() => {
          this.items.push(this.items.length + 1);
          this.isShowLoading = 'hide';
        }, 500);
      },
      onrefresh: function() {
        this.isRefreshing = 'show';
        setTimeout(() => {
          this.items.unshift(this.items[0] - 1);
          this.isRefreshing = 'hide';
        }, 500);
      },
    },
    mounted() {
      console.log(document ? document : weex.document)
      // dom.getComponentRect(this.$refs.inp, option => {
      //   this.hei = option.size.top - 100 + 'px'
      //   console.log('input:', option.size, option.size.top)
      // })
    },
  }
</script>
