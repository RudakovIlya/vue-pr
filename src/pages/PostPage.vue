<template>
  <div>
    <h1>Posts</h1>
    <base-input v-model="searchQuery" class="input" placeholder="Поиск..." />
    <div class="buttons">
      <base-select v-model="selectedSort" :options="sortOptions" />
      <base-button
        :class="{
          disabled: !selectedSort && !searchQuery,
        }"
        @click="clearSort"
      >
        Сбросить фильтры
      </base-button>
    </div>
    <post-list :posts="posts" :is-posts-loading="!isPostsLoading"></post-list>
    <base-pagination
      class="pagination"
      :page="page"
      :total-pages="totalPages"
      @update-page="setPage"
    />
  </div>
</template>

<script>
import { usePosts } from "@/hooks/usePosts";
import PostList from "@/components/PostList.vue";

export default {
  components: { PostList },
  setup() {
    const {
      posts,
      isPostsLoading,
      totalPages,
      searchQuery,
      selectedSort,
      page,
    } = usePosts(4);

    return {
      posts,
      isPostsLoading,
      totalPages,
      selectedSort,
      searchQuery,
      page,
    };
  },
  data() {
    return {
      sortOptions: [
        { value: "title", name: "По названию" },
        { value: "body", name: "По содержимому" },
      ],
    };
  },
  methods: {
    setPage(pageNumber) {
      this.page = pageNumber;
    },
    clearSort() {
      this.selectedSort = "";
      this.searchQuery = "";
    },
  },
};
</script>

<style scoped>
.input {
  margin-top: 15px;
}

.buttons {
  margin: 15px 0;
  display: flex;
  gap: 5px;
  justify-content: flex-end;
}
</style>
