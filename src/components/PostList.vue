<template>
  <div class="post-list">
    <div v-for="post in posts" :key="post.id">
      <SinglePost :post="post" />
    </div>
  </div>
</template>

<script>
import { onMounted, onUnmounted, onUpdated } from "@vue/runtime-core";
import SinglePost from "./SinglePost";
export default {
  props: ["posts"],
  components: { SinglePost },
  setup(props) {
    onMounted(() => {
      console.log("component mounted");
    });
    onUnmounted(() => {
      console.log("component unmounted");
    });
    onUpdated(() => {
      console.log("component updated");
    });
  },
  mounted() {
    console.log('mounted also here');
  }
};
</script>

<style>
</style>