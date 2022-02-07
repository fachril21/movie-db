<template>
  <div class="container mx-auto">
    <div
      class="header w-full rounded-lg bg-blue-500 overflow-hidden relative"
      :style="{
        height: '400px',
        backgroundImage: `url('${baseUrlImg}${movie.backdrop_path}')`,
        backgroundPosition: 'center',
        backgroundSize: '100% auto',
        backgroundRepeat: 'no-repeat',
      }"
    >
      <div
        class="bg-gradient-to-r from-gray-900 to-transparent h-full w-full absolute top-0 left-0"
      >
        <div
          class="h-full w-2/5 flex flex-col items-start justify-center p-8 gap-4"
        >
          <div class="text-3xl font-bold text-white">{{ movie.title }}</div>
          <div class="text-white">{{ movie.overview }}</div>
        </div>
      </div>
    </div>
    <div>{{ movie }}</div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      baseUrlImg: process.env.API_BASE_URL_IMAGE,
    };
  },
  async asyncData(context) {
    return axios
      .get(`${process.env.API_BASE_URL}/movie/${context.params.id}`, {
        params: {
          api_key: process.env.VUE_APP_API_KEY,
        },
      })
      .then((res) => {
        return {
          movie: res.data,
        };
      })
      .catch((error) => {
        context.error(error);
      });
  },
};
</script>
