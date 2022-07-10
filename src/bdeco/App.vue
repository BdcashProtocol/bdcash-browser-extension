<template>
  <div id="app">
    <a id="open" :href="openlink" target="_blank"><i class="fas fa-external-link-alt"></i></a>
    <router-view v-on:onCreatedKey="showBarEmit" ></router-view>
    <div v-if="showbar" class="bottombar">
      <div v-on:click="showDappExplorer()" class="buttonbar">
        dApps Explorer
      </div>
      <div v-on:click="showChangeID()" class="buttonbar">
          Create / Manage Identities
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      id: '',
      openlink: '',
      showbar: false
    }
  },
  mounted (){
    const app = this
    app.id = chrome.runtime.id
    app.openlink = 'moz-extension://' + app.id + '/bdeco/id.html'
    var wallet = localStorage.getItem('$BDCASH_ids');
    if(wallet === null || wallet.length === 0){
      app.showbar = false
    }else{
      app.showbar = true
    }
  },
  methods: {
    showDappExplorer(){
      const app = this
      app.$router.push('explorer')
    },
    showChangeID(){
      const app = this
      app.$router.push('manage')
    },
    showBarEmit(){
      const app = this
      app.showbar = true
    }
  }
}
</script>
<style>
  #app{
    background: #0c0613;
    color: #ffffff;
    min-width:350px;
    width: 100%;
    min-height: 300px;
    padding:20px 20px 70px 20px;
    overflow-y: auto;
    overflow-x: hidden;
    font-family: 'Poppins', sans-serif;
  }
  #open{
    color:#5523a7;
    width:15px;
    height:15px;
    position:fixed;
    top:20px; 
    right:20px;
    font-size:12px;
  }
  h3{
    font-size:20px; 
    margin-top:20px;
    width:100%;
    text-align:center;
  }
  .row{
    padding:0 20px;
    text-align:center;
  }
  .header{
    color:#ffffff;
    font-size:12px; 
    width:100%;
    text-align:center;
    padding:0 0 10px 0;
    border-bottom:1px solid #7222cc;
  }
  .back{
    position:absolute; 
    top:20px; 
    color:rgb(105, 9, 170); 
    left:20px;
  }
  .back:hover{
    color:rgb(172, 68, 233);
    cursor:pointer;
  }
  a{
    color:#4a0b7e!important
  }
  .arrow{
    position:absolute; 
    top:50%; 
    margin-top:-10px; 
    height:20px; 
    right:10px;
  }

  .bottombar{
    position:fixed;
    bottom:0;
    left:0;
    width:100%;
    padding:0 15px;
    border-top:1px solid rgba(140, 71, 185, 0.952);
    background:rgb(98, 44, 185);
    z-index:99;
  }
  .buttonbar{
    width:50%;
    float:left; 
    text-align: center;
    line-height: 40px; 
    height: 40px;
    font-size:12px;
  }
  .buttonbar:hover{
    cursor:pointer;
  }
</style>