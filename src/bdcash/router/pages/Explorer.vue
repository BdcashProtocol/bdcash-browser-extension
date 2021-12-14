<template>
  <div id="explorerpage">
      <i v-on:click="showDashboard" class="fa fa-arrow-left back"></i>  
      <div class="header">
        <strong>dApp Explorer</strong>
      </div> 
      <div v-if="dapps">
        <div v-for="dapp in dapps" v-bind:key="dapp">
          <b-card class="mb-2 mt-2">
            <b-card-text>
              <strong class="dapp-title">{{ dapp.name }}</strong>
              <p>{{ dapp.description }}</p>
            </b-card-text>
            <a class="arrow" target="_blank" :href="'https://' + dapp.link" variant="primary"><i class="fa fa-arrow-right"></i></a>
          </b-card>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      dapps: 
      [
        {
          name: 'Web Wallet',
          description: 'Manage you funds and store data.',
          link: 'wallet.bdcashprotocol.com'
        },
        {
          name: 'ID BDcash Platform',
          description: 'Connect third party identities.',
          link: 'idbdcash.bdcashprotocol.com'
        },
        {
          name: 'Chains Platforms',
          description: 'Create tokens with few clicks.',
          link: 'devs.bdcashprotocol.com'
        },
        {
          name: 'Website Official',
          description: 'Learn more about Project.',
          link: 'bdcashprotocol.com'
        }
      ]
    }
  },
  methods: {
    showDashboard(){
      const app = this
      app.$router.push('dashboard')
    }
  },
  mounted (){
    
  }
}
</script>

<style lang="scss" scoped>
  .dapp-title { font-size: 18px;}
  p {
    font-size: 12px;
    margin-bottom:0px!important
  }
  #explorerpage{
    width:400px;
  }
</style>
