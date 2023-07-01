<template>
  <div class="app font-monospace">
    <div class="content">
      <AppInfo
        :allMovies="movies.length"
        :favouriteMovies="movies.filter((c) => c.favourite).length"
      />
      <div class="search-panel">
        <SearchPanel :updateTermHandler="updateTermHandler" />
        <AppFilter
          :updateFilterHandler="updateFilterHandler"
          :filterName="filter"
        />
      </div>
      <MovieList
        :movies="onFilterHandler(onSearchHandler(movies, term), filter)"
        @onToggle="onToggleHandler"
        @onDelete="onDeleteHandler"
      />
      <MovieForm @createMovie="createMovie" />
    </div>
  </div>
</template>

<script>
import AppInfo from "./components/App-info.vue";
import SearchPanel from "./components/SearchPanel.vue";
import AppFilter from "./components/App-filter.vue";
import MovieList from "./components/Movie-list.vue";
import MovieForm from "./components/Movie-form.vue";

export default {
  components: {
    AppInfo,
    SearchPanel,
    AppFilter,
    MovieList,
    MovieForm,
  },
  data() {
    return {
      movies: [
        {
          id: 1,
          title: "The Shawshank Redemption",
          year: 800,
          like: true,
          favourite: true,
        },
        {
          id: 2,
          title: "The Godfather",
          year: 411,
          like: false,
          favourite: true,
        },
        {
          id: 3,
          title: "The Godfather: Part II",
          year: 501,
          like: true,
          favourite: false,
        },
      ],
      term: "",
      filter: "all",
    };
  },
  methods: {
    createMovie(item) {
      this.movies.push(item);
    },
    onToggleHandler({ id, prop }) {
      this.movies = this.movies.map((item) => {
        if (item.id == id) {
          return { ...item, [prop]: !item[prop] };
        }
        return item;
      });
    },
    onDeleteHandler(id) {
      this.movies = this.movies.filter((item) => item.id != id);
    },
    onSearchHandler(arr, term) {
      if (term.length == 0) {
        return arr;
      }
      return this.movies.filter(
        (item) => item.title.toLowerCase().indexOf(term.toLowerCase()) > -1
      );
    },
    onFilterHandler(arr, filter) {
      switch (filter) {
        case "popular":
          return arr.filter((c) => c.like);
        case "mostViewers":
          return arr.filter((c) => c.year > 500);
        default:
          return arr;
      }
    },
    updateFilterHandler(filter) {
      this.filter = filter;
    },

    updateTermHandler(term) {
      this.term = term;
    },
  },
};
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
