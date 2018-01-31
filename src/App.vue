<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-link to="/">Go to Foo</router-link>
    <router-link to="/content/11">Go to Bar</router-link>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
  @import "./style/main";
</style>
