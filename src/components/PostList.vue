<template>
  <div class="post-list">
    <div v-for="post in posts" :key="post.id">
      <SinglePost :post="post" />
    </div>
  </div>
</template>

<script>
import { onMounted, onUnmounted, onUpdated } from "vue";
import SinglePost from "./SinglePost.vue";
export default {
  props: ["posts"],
  components: { SinglePost },
  setup(props) {
    onMounted(() => console.log("Component on mounted"));
    onUnmounted(() => console.log("Component on unmounted"));
    onUpdated(() => console.log("Component on updated"));
  },
};
</script>

<style></style>
