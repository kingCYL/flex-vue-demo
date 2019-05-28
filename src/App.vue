<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import './assets/font_icons/fonts.css';
export default {
  name: "App"
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
html,
body {
  height: 100%;
  width: 100%;
}
#app {
  height: 100%;
  width: 100%;
}
</style>
