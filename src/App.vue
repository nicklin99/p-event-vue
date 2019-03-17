<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" @click="onClick" ref="logo">
  </div>
</template>

<script>
/* eslint-disable */
import pEvent from 'p-event'
export default {
  name: 'app',
  components: {
    
  },
  methods:{
    onClick(){
      // eslint-disable-next-line
      console.log('onClick')
    }
  },
  mounted(){
    // 浏览器
    pEvent(document, 'DOMContentLoaded').then(()=>{
      // eslint-disable-next-line
      console.log('DOMContentLoaded1')
    })

    const logoEle = this.$refs.logo

    pEvent(logoEle, 'click').then(()=>{
      console.log('logo emit a click event')
    })

    pEvent(this, 'test').then(value=>{
      console.log('app.vue emit a test event, value:', value)
    })

    setTimeout(() => {
      this.$emit('test', 'test event value')
    }, 3000);
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
