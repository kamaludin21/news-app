<template>
  <div>
    <title-section class="px-2 md:px-0" :title="titleSection" />
    <div class="flex h-auto w-full flex-col justify-between space-x-0 md:h-96 md:flex-row md:space-x-2">
      <div
        class="flex h-48 flex-none items-end bg-red-400 bg-cover md:h-auto md:flex-1"
        style="background-image: url('https://images.pexels.com/photos/4110256/pexels-photo-4110256.jpeg?auto=compress)"
      >
        <div class="space-y-2 bg-gradient-to-t from-black/70 p-2">
          <div class="w-fit bg-black/50 px-2">
            <p class="text-white">Bola.net</p>
          </div>
          <p class="text-xl font-bold leading-5 text-slate-200">
            Polisi Ungkap Fakta Baru Hasil Pemeriksaan Indra Kenz di Kasus Binomo
          </p>
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
      />
      <article-lists
        class="hidden h-96 flex-1 md:flex"
        sort-type="Terbaru"
        :category-articles="titleSection"
        :category="titleSection"
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
  }
}
</script>
