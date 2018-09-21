<template>
  <div id="app">
    <Header></Header>
    <div class="main">
        <router-view name="slidebar"></router-view>
        <router-view name="main"></router-view>
    </div>
  </div>
</template>

<script>
import Header from "./components/header";
import PostList from "./components/PostList";
import Slidebar from "./components/SlideBar";
export default {
  name: "App",
  components: {
    Header,
    PostList,
    Slidebar
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
body {
  background-color: #e0e0e0;
  margin: 0px;
}
.main {
  width: 90%;
  max-width: 1400px;
  min-width: 960px;
  margin: 15px auto;
  min-height: 400px;
}
</style>
