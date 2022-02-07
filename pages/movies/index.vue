<template>
  <div class="sm:container sm:mx-auto flex flex-col">
    <section class="popular-movies">
      <div>
        <list-popular-movies :data="popularMovies" />
      </div>
    </section>
    <section class="now-playing-movies">
      <div>
        <list-now-playing-movies :data="nowPlayingMovies" />
      </div>
    </section>
    <section class="top-rated-movies">
      <div>
        <list-top-rated-movies />
      </div>
    </section>
  </div>
</template>

<script>
import ListNowPlayingMovies from "~/components/Movies/ListNowPlayingMovies.vue";
import ListPopularMovies from "~/components/Movies/ListPopularMovies.vue";
import ListTopRatedMovies from "~/components/Movies/ListTopRatedMovies.vue";
export default {
  components: {
    ListPopularMovies,
    ListNowPlayingMovies,
    ListTopRatedMovies,
  },
  data() {
    return {
      popularMovies: [],
      nowPlayingMovies: [],
    };
  },
  methods: {
    async getData() {
      await this.$axios
        .get(`${process.env.API_BASE_URL}/movie/popular`, {
          params: {
            api_key: process.env.VUE_APP_API_KEY,
            page: 1,
          },
        })
        .then((res) => {
          this.popularMovies = res.data.results;
        })
        .catch((error) => {
          console.log(error);
        });

      await this.$axios
        .get(`${process.env.API_BASE_URL}/movie/now_playing`, {
          params: {
            api_key: process.env.VUE_APP_API_KEY,
            page: 1,
          },
        })
        .then((res) => {
          this.nowPlayingMovies = res.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
  mounted() {
    this.getData();
  },
};
</script>
