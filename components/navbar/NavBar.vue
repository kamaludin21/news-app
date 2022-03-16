<template>
  <div class="fixed top-0 z-20 w-full overscroll-none bg-white">
    <div
      class="fixed top-0 left-0 z-50 h-full w-64 transform space-y-0 transition-all ease-in md:hidden"
      :class="show ? 'translate-x-0' : '-translate-x-full'"
    >
      <div class="flex h-full flex-col justify-between bg-white">
        <div class="flex items-center justify-between border-b-2 p-2">
          <img src="~/assets/img/coiled.png" class="h-8 md:h-10" alt="Logo" />
          <button class="text-gray-600 hover:text-teal-600" @click="show = !show">
            <x-icon />
          </button>
        </div>
        <div class="mb-auto space-y-2 p-2">
          <ul class="space-y-1 text-base font-medium">
            <li class="cursor-pointer hover:text-teal-600 hover:underline">News</li>
            <li class="cursor-pointer hover:text-teal-600 hover:underline">Sport</li>
            <li class="cursor-pointer hover:text-teal-600 hover:underline">Technology</li>
            <li class="cursor-pointer hover:text-teal-600 hover:underline">Health</li>
          </ul>
          <hr class="h-2" />
          <div class="flex items-center justify-between rounded-md bg-gray-200 px-2 py-3">
            <p class="text-xs font-semibold text-gray-600">Dark Mode</p>

            <label class="flex cursor-pointer items-center">
              <div class="relative">
                <input id="toggleB" type="checkbox" class="sr-only" />
                <div class="block h-5 w-8 rounded-full bg-gray-600"></div>
                <div class="dot absolute left-1 top-1 h-3 w-3 rounded-full bg-teal-600 transition"></div>
              </div>
            </label>
          </div>
          <button class="w-full rounded-md bg-teal-600 py-2 hover:bg-teal-700 hover:shadow-md">
            <span class="font-medium text-white">LOGIN WITH EMAIL</span>
          </button>
          <div class="py-2">
            <div class="w-full border-b-2"></div>
            <p class="mx-auto -mt-3 w-fit bg-white px-2 text-sm font-light">OR WITH</p>
          </div>
          <div class="flex justify-between">
            <div class="group rounded-md bg-gray-300 p-4 hover:bg-teal-600 hover:shadow-md">
              <google-icon />
            </div>
            <div class="group rounded-md bg-gray-300 p-4 hover:bg-teal-600 hover:shadow-md">
              <twitter-icon />
            </div>
            <div class="group rounded-md bg-gray-300 p-4 hover:bg-teal-600 hover:shadow-md">
              <apple-icon />
            </div>
            <div class="group rounded-md bg-gray-300 p-4 hover:bg-teal-600 hover:shadow-md">
              <facebook-icon />
            </div>
          </div>
        </div>
        <div class="border-t-2 p-2 text-xs font-light text-gray-500">
          <p>2020 &copy; PT. Zyel Bersama Bersinar Network</p>
          <p>Version 1.0</p>
        </div>
      </div>
    </div>
    <div
      v-if="show"
      class="absolute z-40 flex h-screen w-full justify-end overflow-hidden bg-black/70 md:hidden"
      @click="show = !show"
    ></div>
    <main-nabvar @show-searchbar="isSearch = !isSearch" @show-drawer="show = !show" />

    <!-- Search module -->
    <div
      v-show="isSearch"
      class="fixed z-30 flex h-full w-full justify-center bg-black/30 backdrop-blur-sm md:px-10 lg:px-20 xl:px-56"
    >
      <div class="lg:1/3 h-min w-full space-y-2 bg-white py-2 md:w-2/3">
        <div class="flex px-2">
          <input
            type="search"
            placeholder="Pencarian"
            class="flex-1 border border-teal-600 bg-white py-2 px-2 capitalize ring-inset ring-teal-400 focus:outline-none focus:ring-1"
          />
          <button class="bg-teal-600 px-2 hover:bg-teal-700">
            <search-icon class="h-6 w-6 text-white" />
          </button>
        </div>
        <div class="space-y-2 px-2">
          <p class="text-lg font-light">Populer Search</p>
          <div class="flex flex-wrap space-x-2">
            <div
              class="cursor-pointer border-2 border-gray-600 px-1 text-gray-600 hover:border-teal-600 hover:text-teal-600"
            >
              <p class="text-xs font-medium">COVID-10</p>
            </div>
            <div
              class="cursor-pointer border-2 border-gray-600 px-1 text-gray-600 hover:border-teal-600 hover:text-teal-600"
            >
              <p class="text-xs font-medium">KORUPSI</p>
            </div>
            <div
              class="cursor-pointer border-2 border-gray-600 px-1 text-gray-600 hover:border-teal-600 hover:text-teal-600"
            >
              <p class="text-xs font-medium">BPJS</p>
            </div>
            <div
              class="cursor-pointer border-2 border-gray-600 px-1 text-gray-600 hover:border-teal-600 hover:text-teal-600"
            >
              <p class="text-xs font-medium">VIRAL BLAST</p>
            </div>
          </div>
          <!-- <p class="text-lg font-light">Recent search</p>
          <div class="flex rounded-md bg-gray-200 px-2 py-2 hover:bg-gray-300">
            <p class="flex-1 text-sm font-medium leading-4">
              Lorem ipsum dolor sit amet consectetur adi pisicing elit...
            </p>
          </div>
          <div class="flex rounded-md bg-gray-200 px-2 py-2 hover:bg-gray-300">
            <p class="flex-1 text-sm font-medium leading-4">
              Lorem ipsum dolor sit amet consectetur adi pisicing elit...
            </p>
          </div> -->
        </div>
        <div class="flex items-center justify-start space-x-2 border-t-2 px-2 py-3">
          <div class="flex flex-initial items-center">
            <enter-icon class="h-4 w-4" />
            <p class="text-sm">To Enter</p>
          </div>
          <div class="flex flex-initial items-center">
            <up-icon class="h-4 w-4" />
            <down-icon class="h-4 w-4" />
            <p class="text-sm">To Navigate</p>
          </div>
          <div class="flex flex-initial items-center">
            <esc-icon />
            <p class="text-sm">To Close</p>
          </div>
        </div>
      </div>
    </div>

    <category-bar />
  </div>
</template>

<script>
import AppleIcon from '../icons/AppleIcon.vue'
import DownIcon from '../icons/DownIcon.vue'
import EnterIcon from '../icons/EnterIcon.vue'
import EscIcon from '../icons/EscIcon.vue'
import FacebookIcon from '../icons/FacebookIcon.vue'
import GoogleIcon from '../icons/GoogleIcon.vue'
import SearchIcon from '../icons/SearchIcon.vue'
import TwitterIcon from '../icons/TwitterIcon.vue'
import UpIcon from '../icons/UpIcon.vue'
import XIcon from '../icons/XIcon.vue'
import CategoryBar from './CategoryBar.vue'
import MainNabvar from './MainNabvar.vue'
export default {
  name: 'NavBar',
  components: {
    MainNabvar,
    CategoryBar,
    XIcon,
    SearchIcon,
    UpIcon,
    DownIcon,
    EnterIcon,
    EscIcon,
    TwitterIcon,
    AppleIcon,
    GoogleIcon,
    FacebookIcon
  },
  data() {
    return {
      show: false,
      isSearch: false
    }
  }
}
</script>

<style lang="postcss">
input:checked ~ .dot {
  transform: translateX(100%);
  background-color: #48bb78;
}
</style>
