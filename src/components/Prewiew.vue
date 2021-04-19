<template>
  <div class="prewiew">
    <p v-if="isLoading">Loading...</p>
    <ul>
      <li v-for="gif in gifs" :key="gif.id">
        <img :src="gif.images.fixed_height.url" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Prewiew",
  props: {
    gifs: Array,
    isLoading: Boolean,
  },
};
</script>

<style scoped>
.prewiew {
  width: 100%;
}
ul {
  box-sizing: border-box;
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
ul li {
  list-style: none;
  width: 24%;
  height: 250px;
  cursor: pointer;
}
ul li img {
  width: 100%;
  height: 100%;
}
</style>
