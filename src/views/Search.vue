<template>
  <div class="mt-5">
    <!-- <p class="font-weight-black">放送年とクールを選択してください</p> -->
    <Form></Form>
  </div>
</template>

<script>
import axios from 'axios'
import Form from '../components/Form'

export default {
  components:{
    Form,

  },
  created: function () {
    axios.get('http://api.moemoe.tokyo/anime/v1/master/2018')
      .then(response => {
        console.log(response.data) // mockData
        console.log(response.status) // 200
      })
  }
}
</script>

<style>
</style>