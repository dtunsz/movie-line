<template>
  <div>
    <div class="md:flex my-5">
      <img
        :src="movie.Poster"
        alt=""
        class="w-40 h-48 md:w-72 md:h-96 ml-5 md:ml-0"
      />
      <div class="block ml-5">
        <p>Title: {{ movie.Title }}</p>
        <p>Rated: {{ movie.Rated }}</p>
        <p>Release Date: {{ movie.Release }}</p>
        <p>Runtime: {{ movie.Runtime }}</p>
        <p>Actors: {{ movie.Actors }}</p>
        <p>Plot: {{ movie.Plot }}</p>
        <p>IMDB Rating: {{ movie.imdbRating }}</p>
        <p>Language: {{ movie.Language }}</p>
        <p>Awards: {{ movie.Awards }}</p>
        <p>Director(s): {{ movie.Director }}</p>
        <p>Writer: {{ movie.Writer }}</p>
        <p>Country: {{ movie.Country }}</p>
        <p>DVD: {{ movie.DVD }}</p>
        <p>BoxOffice: {{ movie.BoxOffice }}</p>
        <p>Release Year: {{ movie.Year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      movie: {},
    };
  },
  created() {
    this.fetchMovies();
  },

  methods: {
    fetchMovies() {
      var options = {
        method: "GET",
        url: "https://movie-database-imdb-alternative.p.rapidapi.com/",
        params: { r: "json", i: this.$route.params.id },
        headers: {
          "x-rapidapi-host": "movie-database-imdb-alternative.p.rapidapi.com",
          "x-rapidapi-key": "f04c7f2598msh78c34c80c333d1dp1b5f66jsnebec725efe4b"
        }
      };

      axios
        .request(options)
        .then((response) => {
          console.log(response.data);
          this.movie = response.data
        })
        .catch((error) => {
          console.error(error);
        });
    }
  },
  head() {
    return {
      title: this.movie.Title,
      meta: [
        {
          hid: "description",
          name: this.movie.Title,
          content: this.movie.Plot
        }
      ]
    };
  }
};
</script>

<style></style>
