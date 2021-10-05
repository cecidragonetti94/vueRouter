<template>
  <Title text="Title of my blog" />
  <!--<button @click="consumirApi">Consume API</button>-->
  <div class="title-id" v-for="item in arrayBlog" :key="item.id">
    <router-link :to="`/blog/${item.id}`">{{ item.title }}</router-link>
  </div>
</template>

<script>

import Title from "../components/Title.vue";

export default {
  components: {
    Title,
  },
  data: () => ({
    arrayBlog: [],
  }),
  methods: {
    async consumirApi() {
      try {
        const data = await fetch("https://jsonplaceholder.typicode.com/posts");
        const array = await data.json();
        console.log(array);
        this.arrayBlog = array;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
      this.consumirApi()
    },
};
</script>

<style>
</style>