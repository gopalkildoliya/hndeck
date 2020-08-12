<template>
    <div style="height: 100vh; overflow: hidden" class="bg-white">
        <div class="bg-light p-2 border">
            <h2>{{name}}</h2>
        </div>
        <div class="column__list">
            <div v-if="type=='topstories'" class="border p-3 text-center">
                <a href="https://www.producthunt.com/posts/hackernews-deck?utm_source=badge-featured&utm_medium=badge&utm_souce=badge-hackernews-deck" target="_blank"><img src="https://api.producthunt.com/widgets/embed-image/v1/featured.svg?post_id=232165&theme=light" alt="HackerNews Deck - TwitterDeck for Hacker News. Realtime updates. | Product Hunt Embed" style="width: 250px; height: 54px;" width="250px" height="54px" /></a>
            </div>
            <HnItem v-for="item in items.slice(0, 30)" :key="item['.value']" :itemid="item['.value']" class="border border-light p-3"></HnItem>
        </div>
    </div>
</template>

<script>

    import axios from 'axios';
    import {db} from "../db";
    import HnItem from "./HnItem";
    const api = db.ref('v0')
    export default {
        name: "DeckColumn",
        components: {HnItem},
        props: {
            name: {
                type: String
            },
            type: {
                type: String
            }
        },
        data: function () {
            return {
                items: []
            }
        },
/*        firebase: {
            items: db.ref('v0/topstories'),
        },*/
        watch: {
            type: {
                // call it upon creation too
                immediate: true,
                handler(type) {
                    this.$rtdbBind('items', api.child(this.type));
                },
            },
        },
        mounted() {
            /*axios.get('https://hacker-news.firebaseio.com/v0/topstories.json').then(response => {
                console.log(response.data)
                this.items = response.data
            }).catch(error => {
                console.log(error)
            })*/
        }
    }
</script>

<style scoped>
    .column__list {
        height: calc(100vh - 60px);
        overflow: auto;
    }
    .column__list::-webkit-scrollbar-track {
        border-left: 1px solid #e1e8ed;
    }
    .column__list::-webkit-scrollbar-thumb {
        border-radius: 5px;
        background-color: #e1e8ed;
        min-height: 50px;
    }
    .column__list::-webkit-scrollbar {
        width: 10px;
    }
</style>