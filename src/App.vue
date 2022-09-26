<template>
  <div id="app">
    
    <HeaderComponent />
    <div class="loading" v-if="loading">LOADING...</div> <!----BONUS----->
    <MainComponent :cdList='cdCard' />
    
  </div>
</template>

<script>
import axios from 'axios';

import HeaderComponent from './components/HeaderComponent.vue';
import MainComponent from './components/MainComponent.vue';


export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
},
  data() {
    return {
      cdCard : [],
      loading: true,
    }
  },
  created() {
    axios
    .get("https://flynn.boolean.careers/exercises/api/array/music")
    .then((response) => {
      console.log(response)
      this.cdCard = response.data.response;
      this.loading = false 
    })
    
    
  }
  
  


}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Inter+Tight&family=Poppins&family=Roboto:wght@100&display=swap');
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}

.loading {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50% , -50%);
}

img {
  width: 100%;
}
</style>
