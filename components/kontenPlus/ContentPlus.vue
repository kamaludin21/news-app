<template>
  <div class="w-full">
    <title-section class="px-2 md:px-0" title="Report+" subtitle="Special report with afiliat journalist" />
    <div class="hidden-scrollbar flex w-full touch-auto space-x-2 overflow-x-auto overflow-y-hidden pl-2 md:pl-0">
      <div v-for="content in contentPlus" :key="content.id" class="h-min w-3/5 flex-none md:w-1/5 md:flex-1">
        <img class="h-60 w-full object-cover" :src="content.imageUrl" alt="" />
        <div class="mt-2 w-full space-y-1">
          <p v-show="content.newest" class="text-xs font-bold text-red-600">BARU</p>
          <p class="text-lg font-medium capitalize leading-5">{{ content.title }}</p>
        </div>
      </div>
      <div
        class="flex h-60 w-20 flex-none flex-col items-center justify-center rounded-l-lg bg-gray-700 md:hidden md:flex-1"
      >
        <arrow-right-circle-icon size="1.5x" class="text-white"></arrow-right-circle-icon>
        <p class="text-center text-sm font-medium text-white">Jelajah</p>
      </div>
    </div>
  </div>
</template>

<script>
import { ArrowRightCircleIcon } from 'vue-feather-icons'
import TitleSection from '../common/TitleSection.vue'

export default {
  name: 'ContentPlus',
  components: { TitleSection, ArrowRightCircleIcon },
  data() {
    return {
      articles: [],
      contentPlus: [
        {
          id: 1,
          title: 'sejuta mimpi anak langit bersama bintang',
          imageUrl: 'https://images.pexels.com/photos/939702/pexels-photo-939702.jpeg?auto=compress',
          newest: true
        },
        {
          id: 2,
          title: 'Sejuta kapitalis dinegeri komunis',
          imageUrl: 'https://images.pexels.com/photos/4110256/pexels-photo-4110256.jpeg?auto=compress',
          newest: false
        },
        {
          id: 3,
          title: 'Bau busuk di bisnis minyak wangi',
          imageUrl: 'https://images.pexels.com/photos/6108868/pexels-photo-6108868.jpeg?auto=compress',
          newest: false
        },
        {
          id: 4,
          title: 'Melihat hutan, bersama kalimantan',
          imageUrl: 'https://images.pexels.com/photos/6266697/pexels-photo-6266697.jpeg?auto=compress',
          newest: false
        },
        {
          id: 5,
          title: 'Bisakah percaya janji manis para politikus?',
          imageUrl: 'https://images.pexels.com/photos/2070485/pexels-photo-2070485.jpeg?auto=compress',
          newest: false
        }
      ]
    }
  }
}
</script>
