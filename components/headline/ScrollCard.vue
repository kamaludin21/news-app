<template>
  <div class="flex h-min flex-col border-black bg-white shadow">
    <div class="p-2">
      <p class="text-2xl font-bold text-gray-600"><span class="font-extrabold">#</span> TRENDING</p>
    </div>
    <!-- content wrap -->
    <div class="scrollbar overflow-active h-96 w-full overflow-auto">
      <div
        v-for="article in trendingNews.slice(3, 8)"
        :key="article.title"
        class="group articles-center flex items-center space-x-2 p-2 hover:bg-gray-200"
      >
        <img class="h-24 w-2/5 border-white object-cover group-hover:border" :src="article.thumbnail" alt="" />
        <div class="cursor-pointer">
          <p class="text-sm font-medium leading-5">
            {{ article.title }}
          </p>
          <div class="inline-flex items-center">
            <p class="font-base mr-1 text-xs capitalize">{{ article.name }}</p>
          </div>
        </div>
      </div>
    </div>
    <!-- end content -->
    <div class="flex items-center p-2 mb-0.5">
      <button class="flex w-full flex-row items-center">
        <div class="mr-2 bg-gray-600 py-1 px-3 text-white hover:bg-gray-900">
          <ArrowRightIcon class="w-4" />
        </div>
        More on<span class="ml-1 font-semibold">trending</span>
      </button>
    </div>
  </div>
</template>

<script>
import { ArrowRightIcon } from 'vue-feather-icons'
export default {
  name: 'ScrollCard',
  components: { ArrowRightIcon },
  data() {
    return {
      trendingNews: []
    }
  },
  mounted() {
    this.fetchSomething()
  },
  methods: {
    removeString(title) {
      const string = title
      const newsTitle = string.split(' - ')[0]
      return newsTitle;
    },
    async fetchSomething() {
      const PATH_API =
        'https://newsapi.org/v2/top-headlines?country=id&apiKey=6ae7b435d4ed484c842a9d022f2ddaf2&pageSize=8&sortBy=popularity'
      const response = await this.$axios.$get(PATH_API)
      this.trendingNews = response.articles.map((article) => ({
        title: this.removeString(article.title),
        author: article.author,
        thumbnail: article.urlToImage,
        name: article.source.name
      }))
    }
  }
}
</script>

<style lang="postcss" scoped>
</style>
