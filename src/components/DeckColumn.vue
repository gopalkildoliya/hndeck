<template>
    <div style="height: 100vh; overflow: hidden">
        <div class="bg-light p-2 border">
            <h2>{{name}}</h2>
        </div>
        <div class="column__list">
            <HnItem v-for="item in items.slice(0, 30)" :key="item['.value']" :itemid="item['.value']" class="border p-3"></HnItem>
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
</style>