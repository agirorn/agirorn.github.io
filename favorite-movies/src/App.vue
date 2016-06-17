<template>

  <div class="row marketing">
    <ul id="movies">
      <li v-for="movie in movies" class="movie">
        <img class="youtubeIcon"
             v-on:click="play(movie)"
             v-bind:src="youtube">
        <h2>
       {{ movie.name }} ({{ movie.year }})
        </h2>
       <div class="trailer"
             v-bind:class="{ 'show-trailer': movie.showTrailer }">
          <iframe width="560"
                  height="315"
                  v-bind:src="movie.trailer"
                  frameborder="0"
                  allowfullscreen>
          </iframe>
        </div>
      </li>
    </ul>
  </div>
<style>

  .trailer {
    display:none;
  }
  .trailer.show-trailer {
    display: block;
  }
  .youtubeIcon {
    cursor: pointer;
    float:left;
    margin-right: 10px;
  }

  #movies {
    list-style-type: none;
  }
</style>
</template>

<script>

  const _ = require('underscore')
  const movies = require('./movies')
  export default {
    replace: false,
    ready: function() {
      console.log(movies);
      console.log(this._data);
      console.log(this._data.movies);
      console.log(this);
    },
    methods: {
      play: function (movie) {
        movie.showTrailer = !movie.showTrailer;
        console.log('arguments:', arguments)
        console.log('movie:', movie)
        console.log('this:', this)
      }
    },
  	data() {
      return {
        text: 'vue',
        movies: _.map(movies, (movie) => {
          movie.showTrailer = false
          return movie
        }),
        youtube: 'assets/YouTube/48px/YouTube-social-icon_red_48px.png'
      }
    },
    components: {
      // dropdown
    },
  }
</script>
