<template>
  <div class="flex flex-col lg:flex-row place-items-center justify-around py-3 bg-blue-300">
    <h1 class="text-8xl text-black font-thin pb-3 text-center lg:text-left">Montani Shades</h1>
    <nav class="flex flex-row lg:gap-x-14">
      <router-link to="/" class="py-3 px-4 lg:px-10 text-3xl font-thin rounded-lg hover:bg-blue-400 hover:duration-500">Home</router-link>
      <!-- another way to do router links without hardcoding the path -->
      <router-link :to="{ name : 'about' }" class="mx-15 py-3 px-4 lg:px-10 text-3xl font-thin rounded-lg hover:bg-blue-400 hover:duration-500">About</router-link>
      <router-link :to="{ name : 'estimator' }" class="mx-15 py-3 px-4 lg:px-10 text-3xl font-thin rounded-lg hover:bg-blue-400 hover:duration-500">Estimator</router-link>
    </nav>
  </div>
  <router-view/>
</template>

<style>
nav a.router-link-exact-active {
  color: darkblue;
}
</style>
