<template>
  <div>
    <title-section class="px-2 pb-4 md:px-0" :title="titleSection" />
    <div class="flex h-auto w-full flex-col justify-between space-x-0 md:h-96 md:flex-row md:space-x-2">
      <div
        :style="{ backgroundImage: `url('${filterMyArr(articles, 'thumbnail')[0]}')` }"
        class="flex h-48 flex-none items-end bg-red-400 bg-cover bg-center md:h-auto md:flex-1"
      >
        <div class="space-y-2 bg-gradient-to-t via-black from-black p-2">
          <div class="w-fit bg-black/50 px-2">
            <p class="text-white">{{ filterMyArr(articles, 'name')[0] }}</p>
          </div>
          <a :href="filterMyArr(articles, 'url')[0]" class="text-xl font-bold leading-6 text-slate-200">
            {{ filterMyArr(articles, 'title')[0] }}
          </a>
        </div>
      </div>
      <div class="flex md:hidden">
        <article-lists
          class="h-auto w-full"
          sort-type="Trending"
          :category-articles="titleSection"
          :category="titleSection"
        />
      </div>
      <article-lists
        class="hidden h-96 flex-1 md:flex"
        sort-type="Trending"
        :category-articles="titleSection"
        :category="titleSection"
        sort-by-articles="popularity"
      />
      <article-lists
        class="hidden h-96 flex-1 md:flex"
        sort-type="Terbaru"
        :category-articles="titleSection"
        :category="titleSection"
        sort-by-articles="publishedAt"
      />
    </div>
  </div>
</template>

<script>
import ArticleLists from '../common/ArticleLists.vue'
import TitleSection from '../common/TitleSection.vue'

export default {
  name: 'SectionsPage',
  components: { TitleSection, ArticleLists },
  props: {
    titleSection: {
      type: String,
      default: 'General'
    }
  },
  data() {
    return {
      articles: []
    }
  },
  mounted() {
    this.fetchSomething()
  },
  methods: {
    async fetchSomething() {
      const PATH_API =
        'https://newsapi.org/v2/top-headlines?country=id&apiKey=6ae7b435d4ed484c842a9d022f2ddaf2&pageSize=3&sortBy=popularity&category='+this.titleSection+''
      const response = await this.$axios.$get(PATH_API)
      this.articles = response.articles.map((article) => ({
        title: this.removeString(article.title),
        author: article.author,
        url: article.url,
        thumbnail: article.urlToImage,
        name: article.source.name
      }))
    },
    removeString(title) {
      const string = title
      const newsTitle = string.split(' - ')[0]
      return newsTitle;
    },
    filterMyArr(myArr, prop) {
      return myArr.map((obj) => obj[prop])
    },
  }
}
</script>
