<template>
  <v-app>
    <div>
    <v-toolbar
      dark
      prominent
      src="https://cdn.vuetifyjs.com/images/backgrounds/vbanner.jpg"
    >
      <v-app-bar-nav-icon @click="toggleSideMenu"></v-app-bar-nav-icon>

      <v-toolbar-title>Anime Searcher</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-export</v-icon>
      </v-btn>
    </v-toolbar>
  </div>
<v-container fluid fill-height>
    

    <v-navigation-drawer v-model="drawer" absolute temporary>
      <v-list>
        <v-list-item>
          <v-list-item-avatar>
            <img src="https://avatars2.githubusercontent.com/u/1363954?s=460&v=4">
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title>Firebaseから取得した名前</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list-item v-for="(item, index) in items" :key="index">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>
          <router-link v-bind:to="item.name">

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
          </router-link>

        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-container>

    <!-- <SideNav v-bind:drawer="drawer"></SideNav> -->
    <v-layout justify-center>
      <router-view></router-view>
    </v-layout>
  </v-app>
</template>

<script>
// import { mapActions } from 'vuex'
// import SideNav from './components/SideNav'

export default {
  name: 'App',
  components: {
    // SideNav
  },
  data () {
    return {
      drawer: false,
      items: [
                { title: 'アニメ検索', icon: 'mdi-magnify', name: '/about'},
                { title: 'お気に入り', icon: 'mdi-heart' ,name:'/'},

                // { title: '連絡先一覧', icon: 'list' }
            ]
    }
  },
  methods: {
    toggleSideMenu(){
      this.drawer = !this.drawer
      console.log(this.drawer)
    }
  }
}
</script>