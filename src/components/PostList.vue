<template>
  <div v-if="posts.length > 0">
    <post-item
      v-for="post in posts"
      :key="post.id"
      :post="post"
      :is-posts-loading="isPostsLoading"
    />
  </div>
  <h2 v-else-if="isPostsLoading" class="empty">Список постов пуст</h2>
</template>

<script>
import PostItem from "@/components/PostListItem.vue";

export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
    isPostsLoading: {
      type: Boolean,
    },
  },
};
</script>

<style lang="scss" scoped>
.empty {
  text-align: center;
  color: red;
}
</style>
