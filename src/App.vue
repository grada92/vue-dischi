<template>
  <div id="app">
    <HeaderComponent />
    
  </div>
</template>

<script>
import axios from 'axios';

import HeaderComponent from './components/HeaderComponent.vue';


export default {
  name: 'App',
  components: {
    HeaderComponent,
  },
  data() {
    return {
      cdCard : [],
    }
  },
  created() {
    axios
    .get("https://flynn.boolean.careers/exercises/api/array/music")
    .then((response) => {
      console.log(response)
      this.cdCard = response.data.response;

    })
    
    
  }
  
  


}
</script>

<style lang="scss">
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}
</style>
