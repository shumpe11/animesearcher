<template>
<v-container>
<v-layout>
<v-select
          :items="year"
          label="年"
          class="pr-5"
          solo
          v-on:change="test"
        ></v-select>
<v-select
          :items="cours"
          label="クール"
          solo
          v-on:change="test"
        ></v-select>
    <v-btn
      class="mb-5 ml-5"
      outlined
      fab
      color="teal"
    >
      <v-icon>mdi-magnify</v-icon>
    </v-btn>

    </v-layout>
  </v-container>
</template>

<script>
    export default {
        data: () => ({
            year: ['2019', '2018', '2017', '2016', '2015', '2014'],
            cours:['冬','春','夏','秋'],
            searchFlag:0
        }),

        methods:{
            test() {
                this.searchFlag++;
                if(this.searchFlag === 2){
                    console.log("実行")
                    this.searchFlag = 0;
                }else{
                    console.log(this.searchFlag);
                    // this.searchFlag++;
                }
            }
        }
    }

</script>