<template>
  <div id="app" class="container-fluid" style="padding-left: 0px">
    <AppSidebar></AppSidebar>
    <div class="row" style="padding: 0px 15px 0px 95px;">
      <div class="col-md-3 px-1">
        <DeckColumn name="Top News" type="topstories" v-on:show-profile="showProfile = true; profile = $event"/>
      </div>
      <div class="col-md-3 px-1">
        <DeckColumn name="Ask HN" type="askstories" v-on:show-profile="showProfile = true; profile = $event"/>
      </div>
      <div class="col-md-3 px-1">
        <DeckColumn name="Show HN" type="showstories" v-on:show-profile="showProfile = true; profile = $event"/>
      </div>
      <div class="col-md-3 px-1" >
        <DeckColumn name="Jobs" type="jobstories" v-on:show-profile="showProfile = true; profile = $event"/>
      </div>
    </div>
    <UserProfile :show="showProfile" :profile="profile" @hidden="showProfile = false;"></UserProfile>
  </div>
</template>

<script>
import DeckColumn from './components/DeckColumn.vue'
import AppSidebar from './components/AppSidebar.vue'
import UserProfile from "./components/UserProfile";

export default {
  name: 'App',
  data() {
    return {
      showProfile: false,
      profile: null
    }
  },
  components: {
    DeckColumn, AppSidebar, UserProfile
  }
}
</script>

<style>
  @import'~bootstrap/dist/css/bootstrap.css';
  @import '~bootstrap-vue/dist/bootstrap-vue.css';

  body {
    background: #e1e8ed !important;
  }

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
