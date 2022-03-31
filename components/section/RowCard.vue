<template>
  <div class="py-6">
    <title-section class="pl-2 md:pl-0 pb-4" title="Artikel Lain" />
    <div class="hidden-scrollbar flex w-full touch-auto space-x-2 overflow-x-auto overflow-y-hidden pl-2 md:pl-0">
      <div
        v-for="article in trendingNews.slice(0, 4)"
        :key="article.title"
        class="h-min w-4/5 flex-none md:w-1/4 md:flex-1"
      >
        <div
        :style="{ backgroundImage: `url('${article.thumbnail}')` }"
          class="flex h-56 flex-1 items-end border bg-cover"
          
        >
          <div class="bg-gradient-to-t via-black/70 from-black p-2 leading-5">
          <div class="w-fit bg-black/50 px-1 py-0.5 mb-2">
              <p class="text-xs font-semibold text-white">{{ article.name }}</p>
            </div>
            <a :href="article.url" class="font-medium text-slate-200 hover:underline">
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
      const PATH_API = 'https://api-berita-indonesia.vercel.app/tribun/terbaru'
      const response = await this.$axios.$get(PATH_API)
      this.trendingNews = response.data.posts.map((article) => ({
        title: this.removeString(article.title),
        name: this.getStrag(article.link),
        url: article.link,
        thumbnail: article.thumbnail
      }))
    },
    getStrag(title) {
      const string = title
      const category = string.split('/')[3]
      return category;
    },
  }
}
</script>
TitleSection
