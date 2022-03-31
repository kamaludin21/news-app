<template>
  <div class="hidden-scrollbar flex w-full flex-col space-x-0 md:flex-row md:space-x-2">
    <div id="headlineScroll" class="hidden-scrollbar relative h-auto w-full overflow-auto md:w-2/3">
      <div class="grid grid-flow-col md:grid-flow-row">
        <div class="col-span-1 mb-0 w-screen md:col-span-2 md:mb-2 md:w-full">
          
          <news-card class="h-52 w-full md:h-72" :thumbnail-image="filterMyArr(articles, 'thumbnail')[0]">
            <div class="mt-2 inline-flex items-center bg-gray-600/60 w-fit px-2 py-1">
              <p class="font-base mr-1 text-xs capitalize">{{ filterMyArr(articles, 'category')[0] }}</p>
            </div>
            <a :href="filterMyArr(articles, 'url')[0]" target="_blank" class="cursor-pointer text-lg font-bold capitalize leading-6 md:text-2xl">
              {{ filterMyArr(articles, 'title')[0] }}
            </a>
            
          </news-card>
        </div>
        <div class="mr-0 w-screen md:mr-2 md:w-full">
          
          <news-card class="h-52 w-full md:h-48" :thumbnail-image="filterMyArr(articles, 'thumbnail')[1]">
            <div class="mt-2 inline-flex items-center bg-gray-600/60 w-fit px-2 py-1">
              <p class="font-base mr-1 text-xs capitalize">{{ filterMyArr(articles, 'category')[1] }}</p>
            </div>
            <a :href="filterMyArr(articles, 'url')[1]" class="text-lg font-bold capitalize leading-6 md:text-lg md:leading-5">
              {{ filterMyArr(articles, 'title')[1] }}
            </a>
            
          </news-card>
        </div>
        <div class="ml-0 w-screen md:ml-2 md:w-full">
          
          <news-card class="h-52 w-full md:h-48" :thumbnail-image="filterMyArr(articles, 'thumbnail')[2]">
            <div class="mt-2 inline-flex items-center bg-gray-600/60 w-fit px-2 py-1">
              <p class="font-base mr-1 text-xs capitalize">{{ filterMyArr(articles, 'category')[2] }}</p>
              
            </div>
            <a :href="filterMyArr(articles, 'url')[2]" class="text-lg font-bold capitalize leading-6 md:text-lg md:leading-5">
              {{ filterMyArr(articles, 'title')[2] }}
            </a>
            
          </news-card>
        </div>
      </div>
    </div>
    <div class="absolute top-24 flex w-full justify-between pt-14 md:hidden">
      <div class="bg-black/50 py-2 pr-1" @click="scrollLeft()">
        <chevron-left-icon size="1.5x" class="text-white"></chevron-left-icon>
      </div>
      <div class="bg-black/50 py-2 pl-1" @click="scrollRight()">
        <chevron-right-icon size="1.5x" class="text-white"></chevron-right-icon>
      </div>
    </div>
    <scroll-card class="w-full divide-y-2 border-t-4 border-gray-600 bg-white md:w-1/3" />
  </div>
</template>

<script>
import { ChevronLeftIcon, ChevronRightIcon } from 'vue-feather-icons'
import ScrollCard from './ScrollCard.vue'
import NewsCard from './NewsCard.vue'

export default {
  name: 'HeadlinePage',
  components: { NewsCard, ScrollCard, ChevronLeftIcon, ChevronRightIcon },
  data() {
    return {
      leftScroll: 0,
      rightScroll: true,
      ifScrollable: true,
      articles: []
    }
  },
  mounted() {
    this.fetchSomething()
  },
  methods: {
    async fetchSomething() {
      const PATH_API = 'https://api-berita-indonesia.vercel.app/kumparan/terbaru/'
      const response = await this.$axios.$get(PATH_API)
      this.articles = response.data.posts.map((article) => ({
        title: this.removeString(article.title),
        category: this.getStrag(article.link),
        thumbnail: article.thumbnail,
        url: article.link,
      }))
    },
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
    filterMyArr(myArr, prop) {
      return myArr.map((obj) => obj[prop])
    },
    scrollHandler() {
      const scrollbar = document.getElementById('headlineScroll')
      const scrollWitdh = scrollbar.scrollWidth - scrollbar.clientWidth - 2

      if (scrollbar.scrollLeft === 0) {
        this.leftScroll = 0
        this.rightScroll = true
      } else if (scrollbar.scrollLeft >= scrollWitdh) {
        this.rightScroll = false
      } else {
        this.leftScroll = scrollbar.scrollLeft
        this.rightScroll = true
      }
    },
    scrollLeft() {
      const scrollbar = document.getElementById('headlineScroll')
      scrollbar.scrollTo({
        top: 0,
        left: 0,
        behavior: 'smooth'
      })
    },
    scrollRight() {
      const scrollbar = document.getElementById('headlineScroll')
      scrollbar.scrollTo({
        top: 0,
        left: scrollbar.scrollLeft + scrollbar.scrollWidth / 3,
        behavior: 'smooth'
      })
    },
  }
}
</script>

