<template>
  <div class="search">
    <input type="text" v-model="query" @keypress.enter="search" />
    <button @click="search">Search</button>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      query: "",
    };
  },
  methods: {
    search() {
      this.$emit("search:gif", this.query);
    },
  },
};
</script>

<style scoped></style>
