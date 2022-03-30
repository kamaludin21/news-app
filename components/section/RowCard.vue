<template>
  <div class="py-6">
    <title-section class="pb-4" title="Artikel Terkait" />
    <div class="hidden-scrollbar flex w-full touch-auto space-x-2 overflow-x-auto overflow-y-hidden pl-2 md:pl-0">
      <div v-for="article in trendingNews.slice(0, 4)" :key="article.title" class="h-min w-4/5 flex-none md:w-1/4 md:flex-1">
        <div
          class="flex h-56 flex-1 items-end border bg-cover"
          :style="{ backgroundImage: `url('${article.thumbnail}')` }"
        >
          <div class="bg-gradient-to-t from-black/70 p-2">
            <div class="w-fit bg-black/50 px-1 py-0.5 mb-2">
              <p class="text-xs font-semibold text-white">{{ article.name }}</p>
            </div>
            <a :href="article.url" class="text-base hover:underline font-medium text-slate-200 md:text-xl md:leading-5">
              {{ article.title }}
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import TitleSection from '../common/TitleSection.vue'
export default {
  name: 'RowCard',
  components: {
    TitleSection
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
      return newsTitle
    },
    async fetchSomething() {
      const PATH_API =
        'https://newsapi.org/v2/top-headlines?country=id&apiKey=6ae7b435d4ed484c842a9d022f2ddaf2&pageSize=8&sortBy=popularity'
      const response = await this.$axios.$get(PATH_API)
      this.trendingNews = response.articles.map((article) => ({
        title: this.removeString(article.title),
        author: article.author,
        url: article.url,
        thumbnail: article.urlToImage,
        name: article.source.name
      }))
    }
    // errorImage(event) {
    //   event.target.src = img;
    // }
  }
}
</script>
TitleSection
