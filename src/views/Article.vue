<template>
  <div class="article">
    <Title text="path with parameters" />
    <h2>Path:{{ $route.params.id }}</h2>
    <h3>{{ article.title }}----</h3>
    <p>{{ article.id }}--{{ article.body }}</p>
  </div>
</template>

<script>
import Title from '../components/Title';
export default {
  components: {
    Title,
  },
  data: () => ({
    article: {}
  }),
  methods: {
    async consumirArticle() {
      try {
        const data = await fetch(
          `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`);
        const objeto = await data.json();
        console.log(objeto);
        this.article = objeto;
      } catch (error) {
        console.log(error);
      }
    },
  },
  created() {
    this.consumirArticle();
  },
};
</script>

<style>
</style>