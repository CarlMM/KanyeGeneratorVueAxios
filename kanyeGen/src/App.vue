

<template>
  <div>
    <h1>{{ quote }}</h1>
    <h4>- Kanye West</h4>
  </div>
</template>


<script>

import axios from 'axios'
import {ref} from 'vue'


export default {
  setup() {

      const quote = ref('')

      axios.get('https://api.kanye.rest/')
      .then(response =>{
        quote.value = response;
      })

      return {
        quote
      }
  },
}
</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
