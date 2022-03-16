<template>
  <div class="my-0 flex h-full flex-wrap space-y-6 px-0 pt-20 md:my-2 md:px-2 md:pt-24 lg:px-20 xl:px-56">
    <the-headline />
    <content-plus />
    <sections-page title-section="business" />
    <div class="mt-2 w-full space-y-4 border-t-4 border-black bg-white p-2 shadow-md">
      <div class="flex w-full items-center justify-between">
        <p class="text-xl font-bold capitalize md:text-3xl">Video</p>
        <button class="flex items-center space-x-2 hover:text-teal-600">
          <span class="hidden font-medium md:block">Lihat lainnya</span>
          <arrow-right-icon size="1.5x" class="text-lg md:text-base" />
        </button>
      </div>
      <div class="flex space-x-2">
        <div class="flex-1 space-y-2">
          <div
            class="flex h-48 flex-1 items-end border bg-cover"
            style="background-image: url('https://images.pexels.com/photos/4110256/pexels-photo-4110256.jpeg?auto=compress)"
          >
            <div class="group m-2 flex items-center">
              <play-icon
                class="z-10 h-10 w-10 rounded-full bg-gray-800 text-white duration-300 "
              ></play-icon>
              <div
                class="z-0 -ml-2  rounded-md bg-transparent py-0.5 pl-3 pr-2   group-hover:bg-gray-800/70"
              >
                <p class="duration-300 ease-in text-sm group-hover:translate-x-0 -translate-x-full font-semibold text-transparent group-hover:text-white">Play video</p>
              </div>
            </div>
          </div>
          <p class="flex-1 text-lg font-bold capitalize">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet veritatis expedita nisi error
          </p>
        </div>
        <div class="flex-1 space-y-2">
          <div
            class="flex h-48 flex-1 items-end border bg-cover"
            style="background-image: url('https://images.pexels.com/photos/4110256/pexels-photo-4110256.jpeg?auto=compress)"
          >
            <div class="group m-2 flex items-center">
              <play-icon
                class="z-10 h-10 w-10 rounded-full bg-gray-800 text-white duration-300 "
              ></play-icon>
              <div
                class="z-0 -ml-2  rounded-md bg-transparent py-0.5 pl-3 pr-2   group-hover:bg-gray-800/70"
              >
                <p class="duration-300 ease-in text-sm group-hover:translate-x-0 -translate-x-full font-semibold text-transparent group-hover:text-white">Play video</p>
              </div>
            </div>
          </div>
          <p class="text-lg font-bold">Lorem ipsum dolor sit amet consectetur adipisicing elit</p>
        </div>
        <div class="flex-1 space-y-2">
          <div
            class="flex h-48 flex-1 items-end border bg-cover"
            style="background-image: url('https://images.pexels.com/photos/4110256/pexels-photo-4110256.jpeg?auto=compress)"
          >
            <div class="group m-2 flex items-center">
              <play-icon
                class="z-10 h-10 w-10 rounded-full bg-gray-800 text-white duration-300 "
              ></play-icon>
              <div
                class="z-0 -ml-2  rounded-md bg-transparent py-0.5 pl-3 pr-2   group-hover:bg-gray-800/70"
              >
                <p class="duration-300 ease-in text-sm group-hover:translate-x-0 -translate-x-full font-semibold text-transparent group-hover:text-white">Play video</p>
              </div>
            </div>
          </div>
          <p class="text-lg font-bold">
            Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet veritatis expedita
          </p>
        </div>
      </div>
    </div>
    <sections-page title-section="health" />
    <sections-page title-section="technology" />
  </div>
</template>

<script>
import { ArrowRightIcon } from 'vue-feather-icons'
import TheHeadline from '~/components/headline/TheHeadline.vue'
import ContentPlus from '~/components/kontenPlus/ContentPlus.vue'
import SectionsPage from '~/components/section/SectionsPage.vue'
import PlayIcon from '~/components/icons/PlayIcon.vue'
// import TitleSection from '~/components/common/TitleSection.vue'

export default {
  name: 'IndexPage',
  components: {
    TheHeadline,
    ContentPlus,
    SectionsPage,
    ArrowRightIcon,
    // TitleSection
    PlayIcon
  }
}
</script>
