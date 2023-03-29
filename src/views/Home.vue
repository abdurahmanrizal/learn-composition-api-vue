<template>
  <div class="home">
    <h1>Home</h1>
    <!-- <input type="text" v-model="search" />
    <p>Search term - {{ search }}</p>
    <div v-for="name in matchingNames" :key="name">
      {{ name }}
    </div>
    <button @click="handleClick">Stop Watching</button> -->
    <!-- <h2>Refs</h2>
    <p>{{ ninjaOne.name }} - {{ ninjaOne.age }}</p>
    <button @click="updateNinjaOne">Update a ninja one</button>
    <h2>Reactive</h2>
    <p>{{ ninjaTwo.name }} - {{ ninjaTwo.age }}</p>
    <button @click="updateNinjaTwo">Update a ninja two</button> -->
    <!-- <p ref="p">My name is {{ name }} and my age is {{ age }}</p>
    <button @click="handleClick">Click me</button>
    <br />
    <br />
    <button @click="age++">Add 1 to age</button>
    <input type="text" v-model="name" /> -->
    <div v-if="error">
      <p class="error">{{ error }}</p>
    </div>
    <div v-if="posts.length">
      <PostList :posts="posts" v-if="showPosts" />
    </div>
    <div v-else>
      <p>Loading...</p>
    </div>

    <br />
    <button @click="showPosts = !showPosts">Toggle show/hide post</button>
    <button @click="posts.pop()">Delete post</button>
  </div>
</template>

<script>
import { ref, reactive, computed, watch, watchEffect } from "vue";
import PostList from "../components/PostList.vue";
import getPosts from "../composables/getPosts";
export default {
  name: "Home",
  setup() {
    // ref
    // const p = ref(null);
    // data
    // const name = ref("Mario");
    // const age = ref(23);
    // method
    // const handleClick = () => {
    //   // p.value.classList.add("test");
    //   // p.value.textContent = "Hello, ninjas";
    //   name.value = "Luigi";
    //   age.value = 35;
    // };
    // return { name, age, handleClick };
    // const ninjaOne = ref({ name: "Abdurahman", age: 25 });

    // const ninjaTwo = reactive({ name: "Jack", age: 20 });

    // const updateNinjaOne = () => {
    //   ninjaOne.value.age = 30;
    // };

    // // with reactive, we cant do that to property value

    // const updateNinjaTwo = () => {
    //   ninjaTwo.age = 30;
    // };

    // return { ninjaOne, updateNinjaOne, ninjaTwo, updateNinjaTwo };
    // compute property
    // const names = ref([
    //   "mario",
    //   "yoshi",
    //   "luigi",
    //   "toad",
    //   "bowser",
    //   "koopa",
    //   "peach",
    // ]);

    // const search = ref("");

    // const stopWatch = watch(search, () => {
    //   console.log("Watch function ran");
    // });

    // const stopWathcEffect = watchEffect(() => {
    //   console.log("Watch effect function ran");
    // });

    // const matchingNames = computed(() => {
    //   return names.value.filter((name) => name.includes(search.value));
    // });

    // const handleClick = () => {
    //   stopWatch();
    //   stopWathcEffect;
    // };
    // return { names, search, matchingNames, handleClick };
    const { posts, error, load } = getPosts();

    const showPosts = ref(true);
    load();
    return { posts, showPosts, error };
  },

  components: { PostList },
};
</script>
<style scoped>
.error {
  color: red;
  font-size: 15px;
  font-weight: bold;
}
</style>
