<template>
  <form @submit.prevent="onSubmit">
    <input type="text" v-model="name" placeholder="Enter movie name..." class="p-4 w-6/12">
    <input type="submit" value="Search Movies" class="p-4 border border-indigo-300 mx-4 cursor-pointer">
  </form>
</template>

<script>
export default {
  name: "SearchMovies",
  data() {
    return {
      name: ""
    };
  },
  methods: {
    onSubmit() {
      this.$emit("search-name", this.name);
      this.name = "";
    }
  }
};
</script>

<style>
</style>