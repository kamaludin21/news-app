<template>
  <div class="relative border-t border-b px-0 lg:px-20 xl:px-56">
    <div
      id="scrollbar"
      class="nav-scroll flex w-full flex-nowrap items-center justify-between divide-x-2 overflow-x-auto border-x-0 md:border-x-2"
      @scroll="scrollHandler"
    >
      <div
        v-for="category in categories"
        :key="category.id"
        class="group flex w-full cursor-pointer flex-col items-center space-y-1 hover:bg-gray-100"
      >
        <p
          :class="[category.isActive ? 'text-teal-600' : '']"
          class="px-4 pt-2 text-xs font-semibold uppercase group-hover:text-teal-600 md:text-sm"
        >
          {{ category.name }}
        </p>
        <div
          class="h-0.5 w-full group-hover:bg-teal-600"
          :class="[category.isActive ? 'bg-teal-600' : 'bg-transparent']"
        />
      </div>
    </div>
    <div
      v-show="leftScroll > 0"
      class="absolute top-0 left-0 mt-0.5 ml-1 flex items-center rounded-full bg-slate-200 p-1 text-gray-600 shadow-lg hover:text-teal-600 md:hidden"
      @click="scrollLeft()"
    >
      <chevron-left-icon size="1x" class="custom-class"></chevron-left-icon>
    </div>
    <div
      v-show="ifScrollable && rightScroll"
      class="absolute top-0 right-0 mt-0.5 mr-1 flex items-center rounded-full bg-slate-200 p-1 text-gray-600 shadow-lg hover:text-teal-600 md:hidden"
      @click="scrollRight()"
    >
      <chevron-right-icon size="1x" class="custom-class"></chevron-right-icon>
    </div>
  </div>
</template>

<script>
import { ChevronLeftIcon, ChevronRightIcon } from 'vue-feather-icons'
export default {
  name: 'CategoryBar',
  components: { ChevronLeftIcon, ChevronRightIcon },
  data() {
    return {
      leftScroll: 0,
      rightScroll: true,
      ifScrollable: false,
      categories: [
        {
          id: 2,
          isActive: false,
          name: 'News',
          url: '/news'
        },
        {
          id: 1,
          isActive: false,
          name: 'Trending',
          url: '/trending'
        },
        
        {
          id: 3,
          isActive: false,
          name: 'Politic',
          url: '/politic'
        },
        {
          id: 4,
          isActive: false,
          name: 'Health',
          url: '/health'
        },
        {
          id: 5,
          isActive: false,
          name: 'Sport',
          url: '/sport'
        },
        {
          id: 6,
          isActive: false,
          name: 'Otomotif',
          url: '/otomotif'
        }
      ]
    }
  },
  beforeMount() {
    this.checkHor()
  },
  mounted() {
    this.$nextTick(function () {
      this.checkHor()
    })
    window.addEventListener('resize', this.checkHor)
  },
  methods: {
    checkHor() {
      const scrollbar = document.getElementById('scrollbar')
      const hs = this.checkScrollBar(scrollbar, 'horizontal')
      this.ifScrollable = hs
    },
    checkScrollBar(element, dir) {
      dir = dir === 'vertical' ? 'scrollTop' : 'scrollLeft'
      let res = !!element[dir]
      if (!res) {
        element[dir] = 1
        res = !!element[dir]
        element[dir] = 0
      }
      return res
    },
    scrollHandler() {
      const scrollbar = document.getElementById('scrollbar')
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
      const scrollbar = document.getElementById('scrollbar')
      scrollbar.scrollTo({
        top: 0,
        left: 0,
        behavior: 'smooth'
      })
    },
    scrollRight() {
      const scrollbar = document.getElementById('scrollbar')
      scrollbar.scrollTo({
        top: 0,
        left: scrollbar.scrollLeft + scrollbar.scrollWidth / 3,
        behavior: 'smooth'
      })
    }
  }
}
</script>

<style lang="postcss" scoped>
.nav-scroll::-webkit-scrollbar {
  display: none;
}
</style>
