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
        <div class="cursor-pointer grid space-y-1">
          <a :href="article.url" class="text-sm font-medium leading-5">
            {{ article.title }}
          </a>
          <p class="font-base mr-1 text-xs capitalize">{{ article.category }}</p>
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
    getStrag(title) {
      const string = title
      const category = string.split('/')[3]
      return category;
    },
    async fetchSomething() {
      const PATH_API = 'https://api-berita-indonesia.vercel.app/kumparan/terbaru/'
      const response = await this.$axios.$get(PATH_API);
      this.trendingNews = response.data.posts.map((article) => ({
        title: this.removeString(article.title),
        category: this.getStrag(article.link),
        thumbnail: article.thumbnail,
        url: article.link,
      }))
    }
  }
}
</script>