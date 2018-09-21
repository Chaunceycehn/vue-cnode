<template>
    <div class="header">
        <div class="container">
            <router-link :to="{name:'root'}">
                <img src="../assets/cnodejs_light.svg" alt="">
            </router-link>
            <ul class="clearfix">
                <li><a href="#">登录</a></li>
                <li><a href="#">注册</a></li>
                <li><a href="#">关于</a></li>
                <li><a href="#">API</a></li>
                <li><a href="#">新手入门</a></li>
                <li><a href="#">首页</a></li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}

.header {
  background-color: #434343;
}
a {
  color: inherit;
  text-decoration: none;
}

div > a {
  float: left;
  padding: 8px 0px;
  width: 120px;
  height: 34px;
  color: #ccc;
  font-weight: 700;
}
img {
  width: 120px;
}

li {
  list-style: none;
  float: right;
  padding: 14.5px;
}
div > ul > li > a {
  text-decoration: none;
  text-shadow: none;
  color: #ccc;
  font-size: 14px;
}
.container {
  width: 100%;
  min-width: 960px;
  margin: 0 auto;
  max-width: 1400px;
}
</style>
