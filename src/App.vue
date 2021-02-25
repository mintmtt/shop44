<template>
  <div id="app">
    <Header />
    <div class="main">
      <div class="container">
        <div class="row">
          <div class="col-3"></div>
          <div class="col-6" style="padding-bottom: 2rem;"><Cart /></div>
          <div class="col-3"></div>
           <div class="col-12"><Shop /></div>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Header from "./components/Header";
import Shop from "./components/Shop";
import Cart from "./components/Cart";

export default {
  name: "App",
  components: {
    Shop,
    Header,
    Cart,
  },
};
</script>

<style>
#app {
  font-family: Times New Roman, Helvetica, Arial, sans-serif;
  font-size: 15px;
  background-color: rgb(202, 191, 212);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>