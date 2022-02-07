<template>
  <div class="py-2">
    <div class="flex gap-8 justify-between items-center">
      <div class="title font-semibold text-xl">Now Playing</div>
      <div class="flex gap-4">
        <button
          @click="onPrev"
          class="h-8 w-8 rounded-full bg-gray-200 flex items-center justify-center hover:bg-blue-100 hover:text-blue-700 transition-all ease-in-out duration-300 text-xl focus:outline-none"
        >
          <i class="bx bx-chevron-left"></i>
        </button>
        <button
          @click="onNext"
          class="h-8 w-8 rounded-full bg-gray-200 flex items-center justify-center hover:bg-blue-100 hover:text-blue-700 transition-all ease-in-out duration-300 text-xl focus:outline-none"
        >
          <i class="bx bx-chevron-right"></i>
        </button>
      </div>
    </div>
    <div
      id="list-container"
      ref="listContainer"
      class="py-8 flex overflow-hidden gap-4"
    >
      <div class="item" v-for="item in data" :key="item.id">
        <movies-card
          class="w-64"
          :id="item.id"
          :title="item.title"
          :image="item.backdrop_path"
          :vote="item.vote_average"
          :release-date="item.release_date"
        />
      </div>
    </div>
  </div>
</template>

<script>
import MoviesCard from "@/components/Movies/MoviesCard.vue";
export default {
  name: "ListNowPlayingMovies",
  components: {
    MoviesCard,
  },
  props: {
    data: {
      type: Array,
      required: true,
    },
  },
  methods: {
    onNext() {
      this.$refs.listContainer.scrollBy({
        top: 0,
        left: +500,
        behavior: "smooth",
      });
    },
    onPrev() {
      this.$refs.listContainer.scrollBy({
        top: 0,
        left: -500,
        behavior: "smooth",
      });
    },
  },
};
</script>
