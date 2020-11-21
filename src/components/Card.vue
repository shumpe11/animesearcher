<template>
    <v-card
    class="mx-auto"
    hover
    >
        <v-img
        :src="this.Imgurl"
        contain
        height="200px"
        class="white--text align-end"
        gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
        ></v-img>

        <v-card-title class="text-sm-subtitle-1 subtitle-2">
        {{ result.title }}
        </v-card-title>

        <v-card-actions>
            <v-spacer></v-spacer>

            <v-btn icon absolute left>
            <a :href="this.result.public_url" target="_blank" rel="noopener noreferrer">

                <v-icon>mdi-open-in-new</v-icon>
                
            </a>                
            </v-btn>


            <v-btn icon>
                <v-icon>mdi-bookmark</v-icon>
            </v-btn>

            <v-btn icon>
                <v-icon>mdi-heart</v-icon>
            </v-btn>
        </v-card-actions>

    </v-card>
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
a{
    text-decoration: none;
}
</style>