<template>
  <div id="app">
    <div class="header-outer" id="sticky">
      <header>
        <h1 class="site-title"><router-link to="/">kyu-bu's portfolio</router-link></h1>
      </header>
      <hnav></hnav>
      <img src="./assets/logo.png">
      <router-view/>
    </div>
    <transition name="fade">
      <router-view :data="myData"></router-view>
    </transition>
    <fnav></fnav>
    <footer>
      <div class="copyright-box">©︎2019 Kazuki.Saito</div>
    </footer>
  </div>
</template>

<script>
import "bootstrap-vue/dist/bootstrap-vue.css";
import HeaderNav from '@/components/parts/NavHeader'
export default {
  name: 'App',
  components: {
    hnav: HeaderNav
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
