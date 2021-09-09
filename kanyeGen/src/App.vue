

<template>
  <div class="kanyePlacement">
    <div class="kanyeQuotes">
      <h1>{{ quote }}</h1>
      <h3>- Kanye West</h3>
    </div>
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

      // axios.get('https://api.kanye.rest/')
      // .then(response =>{
      //   quote.value = response.data.quote
      // })

      return {
        quote
      }
  },
}
</script>


<style src="./assets/style.css">

</style>
