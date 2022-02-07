<template>
  <div class="cursor-pointer">
    <nuxt-link class="w-full" :to="`/movies/${id}/${slug}`">
      <div
        id="image"
        class="h-32 w-full bg-gray-200 rounded-xl overflow-hidden"
      >
        <img
          class="h-32 w-full object-cover rounded-xl hover:scale-110 transition-all transform ease-in-out duration-300"
          :src="baseUrlImg + image"
          alt=""
        />
      </div>
      <div id="desc" class="w-full flex flex-col gap-2 py-2">
        <div class="flex flex-row items-center gap-2">
          <div
            id="vote"
            class="px-2 bg-yellow-200 rounded-md border border-yellow-500 flex items-center gap-1"
          >
            <i class="bx bxs-star text-yellow-500"></i>
            <span class="text-sm text-gray-700 font-bold">
              {{ vote }}
            </span>
          </div>
          <div class="text-gray-600">•</div>
          <div id="releaseDate" class="text-gray-700 font-bold text-sm">
            {{ formatDate(releaseDate) }}
          </div>
        </div>
        <div class="font-bold text-gray-800">
          <p class="truncate">
            {{ title }}
          </p>
        </div>
      </div>
    </nuxt-link>
  </div>
</template>

<script>
import moment from "moment";
export default {
  name: "MovieCard",
  props: {
    id: {
      type: Number,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
    vote: {
      type: Number,
      required: true,
    },
    releaseDate: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      baseUrlImg: process.env.API_BASE_URL_IMAGE,
    };
  },
  methods: {
    formatDate(date) {
      return moment(date).format("D MMMM YYYY");
    },
  },
  computed: {
    slug() {
      let slug = this.title.replace(/ /g, "-");
      return slug.toLowerCase();
    },
  },
};
</script>
