<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo :allMovies="movies.length" :favouriteMovies="movies.filter(c => c.favourite).length" />
      <div class='search-panel'>
        <SearchPanel />
        <AppFilter />
      </div>
      <MovieList :movies="movies" />
      <MovieForm />
    </div>
  </div>
</template>
data() {
  return {
    movies: [
      {
        id: 1,
        title: 'The Shawshank Redemption',
        year: 1994,
        like: true,
        favourite: true
      },
      {
        id: 2,
        title: 'The Godfather',
        year: 1972,
        like: false,
        favourite: true
      },
      {
        id: 3,
        title: 'The Godfather: Part II',
        year: 1974,
        like: true,
        favourite: false
      }
    ]
  }
},
<script>
import AppInfo from "./components/App-info.vue"
import SearchPanel from "./components/SearchPanel.vue"
import AppFilter from './components/App-filter.vue'
import MovieList from './components/Movie-list.vue'
import MovieForm from './components/Movie-form.vue'

export default {
  components: {
    AppInfo,
    SearchPanel,
    AppFilter,
    MovieList,
    MovieForm
  },
  data() {
    return {
      movies: [
        {
          id: 1,
          title: 'The Shawshank Redemption',
          year: 1994,
          like: true,
          favourite: true
        },
        {
          id: 2,
          title: 'The Godfather',
          year: 1972,
          like: false,
          favourite: true
        },
        {
          id: 3,
          title: 'The Godfather: Part II',
          year: 1974,
          like: true,
          favourite: false
        }
      ]
    }
  },
}
</script>

<style>
.app {
  height: 100vh;
  color: black;
}

.content {
  width: 1000px;
  min-height: 700px;
  background-color: white;
  margin: 0 auto;
  padding: 5rem 10px;
}

.search-panel {
  margin-top: 2rem;
  background-color: #fcfaf5;
  padding: 1.5rem;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>
