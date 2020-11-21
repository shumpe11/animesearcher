<template>
  <v-container fluid>
    <v-row justify="center">
    <!-- <p class="font-weight-black">放送年とクールを選択してください</p> -->
      <v-col cols="12" md="6" sm="8">
        <Form @startSearch="searchAnime"></Form>
      </v-col>
    </v-row>
    <SearchResult :results='this.response'></SearchResult>
  </v-container>
</template>

<script>
import axios from 'axios'
import Form from '../components/Form'
import SearchResult from '../components/SearchResult'


export default {
  components:{
    Form,
    SearchResult

  },
  data: () => ({
    response:{}
  }),
  created: function () {
    
  },
  methods:{
    searchAnime(year, cours){
      // this.response = axios.get('http://api.moemoe.tokyo/anime/v1/master/${this.selected.year}/${this.selected.cours}')
      // console.log(this.response);
      axios.get(`http://api.moemoe.tokyo/anime/v1/master/${year}/${cours}`)
      .then(response => {
        this.response = response.data
        console.log(response.data) // mockData
      })

    }
  }
}
</script>

<style>
</style>