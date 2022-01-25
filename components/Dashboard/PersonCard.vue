<template>
  <div
    class="
      w-40
      h-48
      bg-gray-200
      rounded-xl
      overflow-hidden
      relative
      hover:scale-105
      transition-all
      transform
      ease-in-out
      duration-300
      cursor-pointer
    "
    :style="{
      backgroundImage: 'url(' + baseUrlImg + profilePath + ')',
      backgroundSize: 'cover',
    }"
  >
    <div
      class="
        absolute
        bottom-0
        px-4
        pb-4
        pt-24
        bg-gradient-to-t
        from-gray-900
        to-transparent
        text-white text-sm
        font-bold
        w-full
      "
    >
      {{ name }}
    </div>
  </div>
</template>

<script>
export default {
  name: "PersonCard",
  props: {
    name: {
      type: String,
      required: true,
    },
    profilePath: {
      type: String,
      required: true,
    },
  },
  data() {
    return {
      baseUrlImg: process.env.API_BASE_URL_IMAGE,
    };
  },
};
</script>
