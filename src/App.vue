<template>
  <div id="app">
    <ul class = "hr">
      <li>
        <router-link to ="/">Домой</router-link>
      </li>
      <li>
        <router-link to ="/messages">Кодировка</router-link>
      </li>
       <hr />
    </ul>
    <H1>Закодируйте свое послание</H1>
    <hr />
    <router-view />
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
   ul.hr {
    margin: 0;
    padding: 4px;
    text-align: right;
   }
   ul.hr li {
    display: inline;
    margin-right: 5px;
    border: 1px solid #000; 
    padding: 3px;
   }
</style>
