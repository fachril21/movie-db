<template>
  <div class="py-2">
    <div class="flex gap-8 justify-between items-center">
      <div class="title font-semibold text-xl">Top Rated Movies</div>
    </div>
    <div
      id="list-container"
      ref="listContainer"
      class="py-8 grid grid-cols-5 gap-x-4 gap-y-8"
    >
      <div
        id="list-items"
        ref="listItems"
        class="item"
        v-for="item in topRatedMovies"
        :key="item.id"
      >
        <movies-card
          class="w-full"
          :id="item.id"
          :title="item.title"
          :image="item.backdrop_path"
          :vote="item.vote_average"
          :release-date="item.release_date"
        />
      </div>
    </div>
    <!-- PAGINATION -->
    <div class="w-full flex flex-row justify-between items-center">
      <button
        @click="prevPage"
        class="h-8 w-8 rounded-full bg-gray-200 flex items-center justify-center hover:bg-blue-100 hover:text-blue-700 transition-all ease-in-out duration-300 text-xl focus:outline-none"
      >
        <i class="bx bx-chevron-left"></i>
      </button>
      <div class="font-bold">Page: {{ page }}/{{ totalPages }}</div>
      <button
        @click="nextPage"
        class="h-8 w-8 rounded-full bg-gray-200 flex items-center justify-center hover:bg-blue-100 hover:text-blue-700 transition-all ease-in-out duration-300 text-xl focus:outline-none"
      >
        <i class="bx bx-chevron-right"></i>
      </button>
    </div>
  </div>
</template>

<script>
import MoviesCard from "@/components/Movies/MoviesCard.vue";
export default {
  name: "ListTopRatedMovies",
  components: {
    MoviesCard,
  },

  data() {
    return {
      topRatedMovies: [],
      page: 1,
      totalPages: null,
    };
  },
  methods: {
    async getData() {
      await this.$axios
        .get(`${process.env.API_BASE_URL}/movie/top_rated`, {
          params: {
            api_key: process.env.VUE_APP_API_KEY,
            page: this.page,
          },
        })
        .then((res) => {
          console.log(res);
          this.totalPages = res.data.total_pages;
          this.topRatedMovies = res.data.results;
        })
        .catch((error) => {
          console.log(error);
        });
    },
    nextPage() {
      if (this.page != this.totalPages) {
        this.page = this.page + 1;
        this.getData();
      }
    },
    prevPage() {
      if (this.page > 1) {
        this.page--;
        this.getData();
      }
    },
  },
  mounted() {
    this.getData();
  },
};
</script>
