<template>
  <div class="post">
    <router-link :to="{ name: 'Details', params: { id: post.id } }">
      <h3>{{ post.title }}</h3>
    </router-link>

    <p>{{ snippet }}</p>
    <span v-for="tag in post.tags" :key="tag"> #{{ tag }} </span>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  props: ["post"],
  setup(props) {
    const snippet = computed(() => {
      let a = "";
      if (props.post.body.length > 100) {
        a = props.post.body.substring(0, 100) + "...";
      } else {
        a = props.post.body;
      }
      return a;
    });

    return { snippet };
  },
};
</script>

<style></style>
