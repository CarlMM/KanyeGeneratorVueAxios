

<template>
  
    <div class="kanyeQuotes">
      <h1>{{ quote }}</h1>
      <h3>- Kanye West</h3>
      <button @click="loadQuote">Create Quote</button>
    </div>
  
</template>


<script>

import axios from 'axios'
import {ref} from 'vue'

import KanyeAPI from './services/KanyeAPI'


export default {
  setup() {

      const quote = ref('')

      const loadQuote = async () => {
        const response = await KanyeAPI.getQuote()
        quote.value = response.data.quote
      }

      loadQuote()


      // const createPost = async () => {
      //   const response = await KanyeAPI.createPost(JSON.stringify({
      //     title:'foo',
      //     body:'bar',
      //     usedId:1
        
      //   }))
      //     //const result = await response.data

      //     console.log(response)
        
      //}
      // axios.get('https://api.kanye.rest/')
      // .then(response =>{
      //   quote.value = response.data.quote
      // })

      return {
        loadQuote,
        //createPost,
        quote
      }
  },
}
</script>


<style src="./assets/style.css">

</style>
