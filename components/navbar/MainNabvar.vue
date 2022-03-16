<template>
  <div class="flex flex-row items-center justify-between px-2 py-2 lg:px-20 xl:px-56">
    <button class="block md:hidden hover:text-teal-600" @click="$emit('show-drawer')">
      <menu-icon />
    </button>
    <img src="~/assets/img/coiled.png" class="h-8 md:h-10" alt="Logo" />
    <button class="block md:hidden hover:text-teal-600 mr-2" @click="$emit('show-searchbar')">
      <search-icon class="h-5 w-5" />
    </button>
    <div class="hidden items-center md:flex">
      <button class="hidden md:block hover:text-teal-600 mr-2" @click="$emit('show-searchbar')">
      <search-icon class="h-5 w-5" />
    </button>
      <div class="group relative">
        <div class="flex cursor-pointer items-center space-x-1">
          <span class="font-semibold group-hover:text-red-600">
            <sun-icon class="cursor-pointer text-gray-700 hover:fill-teal-700 hover:text-teal-700" />
          </span>
        </div>
        <div class="absolute left-1/2 hidden -translate-x-1/2 translate-y-0 transform pt-2 group-hover:block z-50">
          <nav class="flex w-max flex-col rounded-lg border bg-white py-1 shadow-md">
            <div class="flex cursor-pointer items-center space-x-2 px-2 py-1 text-teal-600 hover:bg-gray-200">
              <sun-icon class="h-5 w-5" />
              <p class="text-sm font-semibold">LIGHT</p>
            </div>
            <div class="flex cursor-pointer items-center space-x-2 px-2 py-1 hover:bg-gray-200">
              <moon-icon class="h-5 w-5" />
              <p class="text-sm font-semibold">DARK</p>
            </div>
            <div class="flex cursor-pointer items-center space-x-2 px-2 py-1 hover:bg-gray-200">
              <desktop-icon class="h-5 w-5" />
              <p class="text-sm font-semibold">SYSTEM</p>
            </div>
          </nav>
        </div>
      </div>
      <div v-if="isAuth">
        <user-icon class="cursor-pointer text-gray-700 hover:text-teal-700" />
      </div>
      <div v-else>
        <button class="px-4 py-1.5 text-sm font-semibold text-gray-700 hover:text-teal-600">SIGN IN</button>
        <button class="bg-teal-600 px-4 py-1.5 text-sm font-semibold text-white hover:bg-teal-700">SUBSCRIBE</button>
      </div>
    </div>
  </div>
</template>

<script>
import DesktopIcon from '../icons/DesktopIcon.vue'
import MenuIcon from '../icons/MenuIcon.vue'
import MoonIcon from '../icons/MoonIcon.vue'
import SearchIcon from '../icons/SearchIcon.vue'
import SunIcon from '../icons/SunIcon.vue'
import UserIcon from '../icons/UserIcon.vue'
export default {
  name: 'MainNavbar',
  components: { MenuIcon, SearchIcon, SunIcon, MoonIcon, DesktopIcon, UserIcon },
  data() {
    return {
      isAuth: false
    }
  }
}
</script>
