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
            <img src="data:image/jpeg;base64,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">
          </v-list-item-avatar>
          <v-list-item-content>
            <v-list-item-title>name get by firebase</v-list-item-title>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list-item v-for="(item, index) in items" :key="index" :to="item.path">

          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>

            <v-list-item-title>{{ item.title }}</v-list-item-title>

          </v-list-item-content>


        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-layout justify-center>
      <router-view></router-view>
    </v-layout>
    

  </v-container>

    <!-- <SideNav v-bind:drawer="drawer"></SideNav> -->
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
                { title: 'アニメ検索', icon: 'mdi-magnify', path: '/search'},
                { title: 'お気に入り', icon: 'mdi-heart' ,path:'/'},

                { title: '視聴中リスト', icon: 'mdi-heart' ,path:'/'},

                { title: '視聴済みリスト', icon: 'mdi-heart' ,path:'/'},

                // { title: '連絡先一覧', icon: 'list' }
            ]
    }
  },
  methods: {
    toggleSideMenu() {
      this.drawer = !this.drawer
    }
  }
}
</script>

<style lang="scss">
html,
html.overflow-y-hidden {
  overflow-y: scroll !important;
}
</style>