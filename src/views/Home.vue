<template>
  <div class="home">
    <h1>Composition API part 2</h1>
    <div v-if="error">{{ error }}</div>
    <div v-if="posts.length">
      <PostList v-if="showPosts" :posts="posts" />
      <button @click="showPosts = !showPosts">Toggle posts</button>
      <button @click="posts.pop()">delete a post</button>
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostList from "../components/PostList";
import getPosts from "../composables/getPosts";
import { ref } from "@vue/reactivity";

export default {
  name: "Home",
  components: { PostList },
  setup() {
    const { posts, error, load } = getPosts();
    load();

    const showPosts = ref(true);

    return { posts, showPosts, error };
  },
};
</script>
