

<template>
  
    <div class="kanyeQuotes">
      <h1>{{ quote }}</h1>
      <h3>- Kanye West</h3>
      <button @click="createPost">Create Quote</button>
    </div>
  
</template>


<script>

import axios from 'axios'
import {ref} from 'vue'


export default {
  setup() {

      const quote = ref('')

      const loadQuote = async () => {
        const response = await axios.get('https://api.kanye.rest/')
        quote.value = response.data.quote
      }

      loadQuote()


      const createPost = () => {
        axios.post('http://jsonplaceholder.typicode.com/posts',
        JSON.stringify({
          title:'foo',
          body:'bar',
          usedId:1,
        })).then(response => {
          console.log(response)
          quote.value = response.data
        })
      }
      // axios.get('https://api.kanye.rest/')
      // .then(response =>{
      //   quote.value = response.data.quote
      // })

      return {
        createPost,
        quote
      }
  },
}
</script>


<style src="./assets/style.css">

</style>
