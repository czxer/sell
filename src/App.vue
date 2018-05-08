<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab">
       <div class="tab-item">商品</div>
       <div class="tab-item">评论</div>
       <div class="tab-item">商家</div>
    </div>
    <div class="content">
        I am content
    </div>
    <router-view/>
  </div>
</template>

<script>
  import header from './components/header/header.vue';
  const ERR_OK=0;
  export default {
    name: 'App',
    data() {
      return {
        seller:{}
      }
    },
    components:{
     "v-header":header
    },
    created: function () {
      this.$http.get('/api/seller').then(response => {
      // get body data
      response=response.body;
        if(response.errno=== ERR_OK){
           this.seller = response.data;
        }
       }, response => {
      // error callback
      });
    }
  }

</script>

<style>
  .tab{width:100%;display:flex;}
 .tab-item{flex:1;text-align:center;padding:15px 0;}
</style>
