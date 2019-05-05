<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro:400,700');

#app {
  height: 100%;
  .loading {
    position: fixed;
    height: 100%;
    width: 100%
  }
}

html, body {
  height: 100%;
  background: hsl(205, 15, 15);
  margin: 0;
  color: white;
  font-family: 'Source Sans Pro', sans-serif;
}
.button {
  font-family: 'Source Sans Pro', sans-serif;
  font-size: 16px;
}
</style>
