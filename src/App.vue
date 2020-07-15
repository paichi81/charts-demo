<template lang="pug">
  v-app
    v-app-bar(
      app
      dense
      flat
      color="primary white--text "
    )
      v-app-bar-nav-icon
        v-icon(color="warning darken-1") fa fa-home
      v-toolbar-title グラフ描画デモ
      v-toolbar-items
      v-spacer
      v-toolbar-items
        span hoge
      v-app-bar-nav-icon
        v-icon(color="orange") fa fa-sun fa-spin

    v-container(fluid)#nv.mt-8
      v-row(no-gutters)
        v-col
          v-tabs(
            centered
            active-class="info white--text"
          )
            v-tab(to="/")
              span Home
            v-tab(to="/vuetify")
              span Vuetify
            v-tab(to="/charts")
              span charts.js
            v-tab(to="/apexcharts")
              span apexcharts
            v-tab(to="/chartist")
              span chartist
            v-tab(to="/about")
              span About

    router-view
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
