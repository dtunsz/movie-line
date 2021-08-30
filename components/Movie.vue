<template>
  <nuxt-link :to="'movies/' + movie.imdbID">
    <div class="flex my-5">
      <img :src="movie.Poster" alt="" class="w-32 h-42 md:w-56 md:h-72" />
      <div class="block ml-5">
        <p>Title: {{ movie.Title }}</p>
        <p>Release Year: {{ movie.Year }}</p>
      </div>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  name: "Movie",

  props: {
    movie: {
      type: Object,
      required: true
    }
  },
};
</script>

<style>
.movie {
  padding: 1rem;
  border: 1px dotted #ccc;
  margin: 1rem 0;
}
</style>
