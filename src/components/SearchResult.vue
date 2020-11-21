<template>
<v-container>
  <!-- 画面サイズsm以外(601px以上)はCardを使い検索結果を表示 -->
  <v-row v-if="width > 600">
    <v-col cols="12" sm="6" md="4"
      v-for="(result, key) in results"
      v-bind:key="key">
        <Card
          v-bind:result="result"
        ></Card>
    </v-col>
  </v-row>

  <!-- 画面サイズsmはListを使い検索結果を表示 -->
  <v-row v-else>
    <v-list three-line>
      
      <Listitem
          v-for="(result, key) in results"
          v-bind:result="result"
          v-bind:key="key"
          ></Listitem>
          
    </v-list>
  </v-row>

  </v-container>
</template>

<script>
import Card from "./Card"
import Listitem from "./Listitem"

export default {
  components:{
    Card,
    Listitem
  },

  props:{
    'results':{
      type:[Object, Array]
    }
  },

  data: () => ({
    width: window.innerWidth
  }),

  methods: {
    // resizeのたび発火する。
    // dataのwidthを更新
    handleResize: function() {
      this.width = window.innerWidth;
    }
  },

  mounted () {
    window.addEventListener('resize', this.handleResize)
  },

  beforeDestroy () {
    window.removeEventListener('resize', this.handleResize)
  }

}


</script>

<style></style>
