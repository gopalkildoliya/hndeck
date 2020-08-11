<template>
    <div style="background: rgb(246, 246, 239)">
        <div v-if="item">
            <a :href="item.url" class="text-dark">{{item.title}}</a>
            <br>
            <div class="text-secondary">
                <small>{{item.score}} points by {{item.by}} {{time}} | {{item.descendants}} comments | <a :href="link" target="_blank" class="text-secondary">discuss</a></small>
            </div>
        </div>
    </div>

</template>

<script>
    import moment from 'moment';
    import {db} from "../db";
    const items = db.ref('v0/item')
    export default {
        name: "HnItem",
        props: ['itemid'],
        data() {
            return {
                item: null
            }
        },
        watch: {
            itemid: {
                // call it upon creation too
                immediate: true,
                handler(id) {
                    this.$rtdbBind('item', items.child(id))
                },
            },
        },
        computed: {
            link() {
                return "https://news.ycombinator.com/item?id=" + this.itemid
            },
            time() {
                return moment(this.item.time, 'X').fromNow()
            }
        }
    }
</script>

<style scoped>

</style>