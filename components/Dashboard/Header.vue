<template>
  <div class="h-16">
    <header class="h-full flex items-center sm:container sm:mx-auto">
      <div class="navigation-items">
        <ul class="nav-list flex gap-8">
          <li
            class="nav-item text-gray-500 font-md hover:text-gray-800 transition-all ease-in-out duration-300"
            :class="{ 'text-gray-800 font-bold': $route.path == '/' }"
          >
            <nuxt-link to="/">Home</nuxt-link>
          </li>
          <li
            class="nav-item text-gray-500 font-md hover:text-gray-800 transition-all ease-in-out duration-300"
            :class="{ 'text-gray-800 font-bold': $route.path == '/movies' }"
          >
            <nuxt-link to="/movies">Movies</nuxt-link>
          </li>
          <li
            class="nav-item text-gray-500 font-md hover:text-gray-800 transition-all ease-in-out duration-300"
            :class="{ 'text-gray-800 font-bold': $route.path == '/tv-series' }"
          >
            <nuxt-link to="/tv-series">TV Series</nuxt-link>
          </li>
        </ul>
      </div>
    </header>
  </div>
</template>

<script>
export default {
  name: "Header",
  components: {},
  data() {
    return {};
  },
};
</script>

<style scoped>
.nav-item {
  margin: 0 10px;
}

.nav-item a {
  text-decoration: none;
}
</style>
