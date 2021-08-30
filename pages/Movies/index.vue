<template>
  <div>
    <SearchMovie @search-name="fetchMovies"/>
    <div v-if="movies.length" class="my-6">
        <p class="text-3xl text-center">Search Results</p>
        <Movie v-for="movie in movies" :key="movie.imdbID" :movie="movie"/>
    </div>
    <div v-if="!movies.length && !isFetching" class="mt-20 text-center">
        <p>No Results, Please enter movie name and click the <strong>Search Movies</strong> button</p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Movie from "../../components/Movie";
import SearchMovie from "../../components/SearchMovie";
export default {
  components: {
    Movie,
    SearchMovie
  },
  data() {
    return {
      movies: [],
      isFetching: false,
    };
  },

  methods: {

    fetchMovies(text) {
        this.isFetching = true;
        var options = {
        method: 'GET',
        url: 'https://movie-database-imdb-alternative.p.rapidapi.com/',
        params: {s: text, r: 'json',},
        headers: {
            'x-rapidapi-host': 'movie-database-imdb-alternative.p.rapidapi.com',
            'x-rapidapi-key': 'f04c7f2598msh78c34c80c333d1dp1b5f66jsnebec725efe4b'
        }
        };

        axios.request(options).then((response) => {
            console.log(response.data)
            this.movies = response.data.Search
        }).catch((error) => {
            console.error(error);
        });
        this.isFetching =false
    }
  },
  head() {
    return {
      title: "Movie Line",
      meta: [
        {
          hid: "description",
          name: "Movie Line",
          content: "Best place to search movies using IMDB database"
        }
      ]
    };
  }
};
</script>

<style>
</style>