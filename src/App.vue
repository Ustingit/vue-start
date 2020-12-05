<template>
  <div id="app">
    <h1>TODO application</h1>
    <hr />
    <router-view /> <!-- сюда вью рендерит компоненты от роутинга -->
  </div>
</template>



<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
