<template>
  <div class="main-container">
    <input
      class="input"
      v-model="searchTerm"
      type="text"
      placeholder="Search"
    />
    <div v-if="searchTerm">
      <p v-for="item in filteredData" :key="item.id">{{ item.title }}</p>
    </div>
  </div>
</template>

<script>
import data from "./components/search.json";

export default {
  data() {
    return {
      items: data,
      searchTerm: "",
    };
  },
  computed: {
    filteredData() {
      return this.items.filter((item) => {
        return item.title.toLowerCase().includes(this.searchTerm.toLowerCase());
      });
    },
  },
};
</script>
