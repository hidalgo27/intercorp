<template>

  <img src="./assets/intercorp.png" alt="" class="mx-auto p-6">

  <div id="nav" class="container mx-auto my-12 font-bold p-6 text-center shadow-lg rounded-2xl bg-gray-50 m-auto">
    <router-link to="/" class="font-bold text-blue-500">Home</router-link> |
    <router-link to="/about" class="font-bold text-blue-300">Quienes somos</router-link>
<!--    <router-link to="/contact" class="font-bold text-blue-500">Contact</router-link>-->
  </div>

  <router-view></router-view>
</template>

<style>
#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
