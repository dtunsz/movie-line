<template>
  <div class="container section_bg_gray relative z-10 max-w-screen-lg xl:max-w-screen-xl mx-auto">
    <Navbar/>
    <nuxt/>
  </div>
</template>

<script>
import Navbar from "../components/Navbar";
export default {
  components: {
    Navbar
  }
};
</script>


<style>
* {
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 1rem;
  line-height: 1.6;
  background: #f4f4f4;
}
a {
  color: #666;
  text-decoration: none;
}
</style>