<template>
  <div class="flex h-min flex-col border-t-4 border-black bg-white shadow">
    <div class="p-2 w-full border-b-2">
      <p class="text-base text-gray-800 font-bold">{{ sortType }} di <span class="capitalize">{{ category }}</span></p>
    </div>
    <div class="scrollbar overflow-active h-96 w-full overflow-auto">
      <div
        v-for="article in trendingNews.slice(3, 8)"
        :key="article.title"
        class="group articles-center flex items-center space-x-2 p-2 bg-slate-50 hover:bg-gray-200"
      >
        <img class="h-20 w-1/4 border-white object-cover group-hover:border" :src="article.thumbnail" alt="" />
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
  </div>
</template>

<script>
export default {
  name: 'ArticleLists',
  components: {  },
  props: {
    categoryArticles: {
      type: String,
      default: 'sports'
    },
    sortByArticles: {
      type: String,
      default: 'publishedAt'
    },
    sortType: {
      type: String,
      default: 'Kosong'
    },
    category: {
      type: String,
      default: 'Kosong'
    },
  },
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
      const category = this.categoryArticles;
      const sortBy = this.sortByArticles;
      const PATH_API =
        'https://newsapi.org/v2/top-headlines?country=id&apiKey=6ae7b435d4ed484c842a9d022f2ddaf2&pageSize=8&sortBy=popularity&category='+category+'&sortBy='+sortBy+''
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