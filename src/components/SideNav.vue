<template>

    <v-layout wrap style="height: 200px;" >

        <v-navigation-drawer app v-model="drawer" absolute temporary>
            <!-- <v-list class="pa-1">
                <v-list-tile avatar>
                    <v-list-tile-avatar>
                    </v-list-tile-avatar>
                    <v-list-tile-content>
                        <v-list-tile-title>Firebaseから取得したユーザー名</v-list-tile-title>
                    </v-list-tile-content>
                </v-list-tile>
            </v-list>

            <v-list class="pt-0" dense>
                <v-divider></v-divider>
                <v-list-tile v-for="item in items" :key="item.title">
                    <v-list-tile-action>
                        <v-icon>{{ item.icon }}</v-icon>
                    </v-list-tile-action>
                    <v-list-tile-content>
                        <v-list-tile-title>{{ item.title }}</v-list-tile-title>
                    </v-list-tile-content>
                </v-list-tile>
            </v-list> -->
        </v-navigation-drawer>

    </v-layout>
</template>

<script>
export default {
    props: {
        drawer:Boolean
    },

    data () {
        return {
            // drawer:false,
            items: [
                { title: '連絡先一覧', icon: 'list' },
                { title: '連絡先一覧', icon: 'list' }
            ]
        }
    }
}
</script>