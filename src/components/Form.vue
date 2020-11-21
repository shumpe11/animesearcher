<template>
<!-- <v-container> -->
<v-layout>
<v-select
          :items="year"
          label="年"
          class="pr-5"
          solo
          v-model="selected.year"
        ></v-select>
<v-select
          :items="cours"
          label="クール"
          solo
          v-model="selected.cours"
        ></v-select>
    <v-btn
      class="mb-5 ml-5"
      outlined
      fab
      color="teal"
    >
      <v-icon @click="clickMagnify">mdi-magnify</v-icon>
    </v-btn>

    </v-layout>
  <!-- </v-container> -->
</template>

<script>
    export default {
        data: () => ({
            year: ['2020', '2019', '2018', '2017', '2016', '2015', '2014'],
            cours:['冬','春','夏','秋'],
            searchFlag:0,
            selected:{year:'', cours:''},
            searchResult:{},
        }),
        methods:{
            // test() {
            //     this.searchFlag++;
            //     if(this.searchFlag === 2){
            //         console.log("実行")
            //         this.searchFlag = 0;
            //     }else{
            //         console.log(this.searchFlag);
            //         // this.searchFlag++;
            //     }
            // },
            clickMagnify(){
              switch (this.selected.cours){
                case '春': this.selected.cours=1; break;
                case '夏': this.selected.cours=2; break;
                case '秋': this.selected.cours=3; break;
                case '冬': this.selected.cours=4; break;
              }
              this.$emit('startSearch', this.selected.year, this.selected.cours)
              switch (this.selected.cours){
                case 1: this.selected.cours='春'; break;
                case 2: this.selected.cours='夏'; break;
                case 3: this.selected.cours='秋'; break;
                case 4: this.selected.cours='冬'; break;
              }
            }
        }
    }
</script>