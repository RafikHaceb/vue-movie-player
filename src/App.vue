<template>
  <div id="app">
    <el-container>
      <el-main>
        <player-viewer :movie="selectedMovie"></player-viewer>
      </el-main>
      <el-footer height="220px">
        <player-footer :availbleMovies="movies" @selectMovie="playMovie"></player-footer>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
import PlayerViewer from './components/PlayerViewer'
import PlayerFooter from './components/PlayerFooter'

export default {
  name: 'App',
  data : function () {
    return {
      movies: [],
      selectedMovie: { trailer: "" }
    }
  },
  components : {
    'player-viewer': PlayerViewer,
    'player-footer': PlayerFooter
  },
  methods: {
    playMovie: function (payload) {
      this.selectedMovie = this.movies[payload.index];
    }
  },
  created: function () {
    this.$http.get('https://scotch-mvplayer-api.herokuapp.com/api/v1').then(response => {
      this.movies = response.body;
      if (this.movies.length > 0) {
        this.selectedMovie = this.movies[0];
      }
    });
  }
}
</script>

<style>
.el-container{
    width: 60%;
    margin: 0 auto;
    background-color: #000;
}
.el-main {
  padding-bottom: 0;
}
</style>