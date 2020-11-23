<template>
  <div id="app">
    <h1 class="animated-word">Todo application</h1>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: "Open Sans", sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.animated-word {
  font-weight: 600;
  text-align: center;
  color: #2c3e50;
  cursor: pointer;
  width: 100%;
}
.animated-word:hover {
  color: rgba(71, 126, 232, 0.7);
}
</style>
