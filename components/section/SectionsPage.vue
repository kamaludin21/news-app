<template>
  <div>
    <title-section class="px-2 pb-4 md:px-0" :title="titleSection" />
    <div class="flex h-auto w-full flex-col justify-between space-x-0 md:h-96 md:flex-row md:space-x-2">
      <div
        :style="{ backgroundImage: `url('${filterMyArr(articles, 'thumbnail')[0]}')` }"
        class="flex h-48 flex-none items-end bg-red-400 bg-cover bg-center md:h-auto md:flex-1"
      >
        <div class="bg-gradient-to-t via-black/70 from-black/80 p-2">
          <a :href="filterMyArr(articles, 'url')[0]" class="text-xl font-bold leading-6 text-slate-200">
            {{ filterMyArr(articles, 'title')[0] }}
          </a>
        </div>
      </div>
      <div class="flex md:hidden">
        <article-lists
          class="h-auto w-full"
          :category=titleSection
          source="tempo"
        />
      </div>
      <article-lists
        class="hidden h-96 flex-1 md:flex"
        :category=titleSection
        :source=sourceOne
      />
      <article-lists
        class="hidden h-96 flex-1 md:flex"
        :category=titleSection
        :source=sourceTwo
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
    },
    sourceOne: {
      type: String,
      default: 'General'
    },
    sourceTwo: {
      type: String,
      default: 'General'
    },
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
      const PATH_API = 'https://api-berita-indonesia.vercel.app/'+this.sourceOne+ '/' + this.titleSection
      console.log(PATH_API)
      const response = await this.$axios.$get(PATH_API)
      this.articles = response.data.posts.map((article) => ({
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
