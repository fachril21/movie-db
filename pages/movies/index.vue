<template>
  <div class="sm:container sm:mx-auto">
    <section class="popular-movies">
      <div>
        <list-popular-movies :data="popularMovies" />
      </div>
    </section>
  </div>
</template>

<script>
import ListPopularMovies from "~/components/Movies/ListPopularMovies.vue";
export default {
  components: {
    ListPopularMovies,
  },
  asyncData({ $axios }, callback) {
    $axios
      .get(`${process.env.API_BASE_URL}/movie/popular`, {
        params: {
          api_key: process.env.VUE_APP_API_KEY,
          page: 1,
        },
      })
      .then((res) => {
        callback(null, { popularMovies: res.data.results });
        console.log(res);
      });
  },
};
</script>
