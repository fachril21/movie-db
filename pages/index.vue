<template>
  <div class="sm:container sm:mx-auto">
    <section class="popular-artists">
      <div>
        <list-popular-artist :data="popularArtist" />
      </div>
    </section>
  </div>
</template>

<script>
import ListPopularArtist from "~/components/Dashboard/ListPopularArtist.vue";
export default {
  components: {
    ListPopularArtist,
  },
  asyncData({ $axios }, callback) {
    $axios
      .get(`${process.env.API_BASE_URL}/person/popular`, {
        params: {
          api_key: process.env.VUE_APP_API_KEY,
          page: 1,
        },
      })
      .then((res) => {
        callback(null, { popularArtist: res.data.results });
        console.log(res);
      });
  },
};
</script>
