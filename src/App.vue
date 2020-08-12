<template>
  <div id="app" class="container-fluid" style="padding-left: 0px">
    <AppSidebar></AppSidebar>
    <div class="row" style="padding: 0px 15px 0px 95px;">
      <div class="col-md-3 px-1">
        <DeckColumn name="Top News" type="topstories"/>
      </div>
      <div class="col-md-3 px-1">
        <DeckColumn name="Ask HN" type="askstories"/>
      </div>
      <div class="col-md-3 px-1">
        <DeckColumn name="Show HN" type="showstories"/>
      </div>
      <div class="col-md-3 px-1" >
        <DeckColumn name="Jobs" type="jobstories"/>
      </div>
    </div>

  </div>
</template>

<script>
import DeckColumn from './components/DeckColumn.vue'
import AppSidebar from './components/AppSidebar.vue'

export default {
  name: 'App',
  components: {
    DeckColumn, AppSidebar
  }
}
</script>

<style>
  @import'~bootstrap/dist/css/bootstrap.css';
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
