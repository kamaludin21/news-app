<template>
  <div class="flex h-min flex-col border-t-4 border-black bg-white shadow">
    <div class="w-full border-b-2 p-2">
      <p class="text-base font-bold text-gray-800 capitalize">
        {{ category }} <span class="lowercase">di</span> {{ source }}
      </p>
    </div>
    <div class="scrollbar overflow-active h-96 w-full overflow-auto">
      <div
        v-for="article in trendingNews.slice(2, 7)"
        :key="article.title"
        class="group articles-center flex items-start space-x-2 bg-slate-50 p-2 hover:bg-gray-200"
      >
        <img
          class="h-20 w-1/4 border-white object-cover group-hover:border"
          :src="article.thumbnail"
          alt=""
          @error="errorImage"
        />
        <div class="cursor-pointer leading-4">
          <a :href="article.url" class="text-sm font-medium">
            {{ article.title }}
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import img from 'assets/img/error.webp'
export default {
  name: 'ArticleLists',
  components: {},
  props: {
    category: {
      type: String,
      default: 'Kosong'
    },
    source: {
      type: String,
      default: 'Kosong'
    }
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
      const result = string.split(' - ')[0]
      return result
    },
    getStrag(title) {
      const string = title
      const result = string.split('/')[3]
      return result
    },
    async fetchSomething() {
      const PATH_API = 'https://api-berita-indonesia.vercel.app/' + this.source + '/' + this.category
      const response = await this.$axios.$get(PATH_API)
      this.trendingNews = response.data.posts.map((article) => ({
        title: this.removeString(article.title),
        name: this.getStrag(article.link),
        url: article.link,
        thumbnail: article.thumbnail
      }))
    },
    errorImage(event) {
      event.target.src = img
    }
  }
}
</script>
