<template>
    <div>
      <h1>Welcome To The Book Page</h1>
      <div v-for="book in books" :key="book.id">
        <div  v-html="book.excerpt.rendered"/>
       <NuxtLink :to="`/book/${book.slug}`"> {{book.title.rendered}} </NuxtLink>
      </div>
    </div>

</template>

<script>
export default {

  data: () => ({
    books: []
  }),
  async fetch() {
    const response = await this.$axios.get('/wp-json/wp/v2/books')
    this.books = response.data
  },
  fetchOnServer: true
}
</script>

<style>

</style>
