<template>
<a :href="this.result.public_url">
<v-col cols="12">
    <v-list-item>
        <v-list-item-avatar>
            <v-img :src="this.Imgurl"></v-img>
        </v-list-item-avatar>

        <v-list-item-content>
            <v-list-item-title v-if="result.title.length <= 14" class="subtitle-2">{{ result.title }}</v-list-item-title>
            <v-list-item-title v-else class="subtitle-2">{{ result.title.slice(0, 14) }} <br> {{ result.title.slice(14) }}</v-list-item-title>

            <!-- <v-list-item-subtitle v-html="item.subtitle"></v-list-item-subtitle> -->
        </v-list-item-content>
    </v-list-item>
    <v-divider></v-divider>
</v-col>
</a>
</template>

<script>
    export default {
        props:{
            'result':{
                type:[Object, Array]
            }
        },

        data: () => ({
            Imgurl:"",
        }),

        created () {
            const CORS_PROXY = 'https://cors-anywhere.herokuapp.com/'
            const url = CORS_PROXY + this.result.public_url
                fetch(url)
                    .then((response) => response.text())
                    .then((text) => {
                        const el = new DOMParser().parseFromString(text, 'text/html')
                        const headEls = el.head.getElementsByTagName("meta");
                        Array.from(headEls).map((v) => {
                            let prop = v.getAttribute('property')
                            if (!prop || prop != "og:image") return;
                            else if(v.getAttribute('content').match(/jpg/) || 
                                    v.getAttribute('content').match(/png/)){
                                        this.Imgurl = v.getAttribute('content');
                            }
                        })
                })         
        },

        methods:{

        }
    }
</script>
<style>

</style>