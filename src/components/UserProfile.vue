<template>
    <div>
        <b-sidebar id="sidebar-right" v-model="show" title="User" @hidden="$emit('hidden')" right shadow>
            <div class="px-3 py-2" v-if="user">
                <div class="text-center">
                    <h1 class="text-center">{{user.id}}</h1>
                    <b-button variant="primary">
                        Karma
                        <b-badge variant="light">{{user.karma}} <span class="sr-only">karma</span></b-badge>
                    </b-button>
                    <p class="pt-3" v-html="user.about">                    </p>
                </div>

            </div>
        </b-sidebar>
    </div>
</template>

<script>
    import {db} from "../db";
    const users = db.ref('v0/user')
    export default {
        name: "UserProfile",
        props: ['show', 'profile'],
        data() {
            return {
                user: null
            }
        },
        watch: {
            profile: {
                // call it upon creation too
                immediate: true,
                handler(id) {
                    this.$rtdbBind('user', users.child(id))
                },
            },
        },
    }
</script>

<style scoped>

</style>