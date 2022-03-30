<template>
  <div class="flex flex-col bg-slate-200">
    <nav-bar />
    <Nuxt />
    <TheFooter class="mt-auto"/>
  </div>
</template>

<script>
import NavBar from '~/components/navbar/NavBar.vue'
import TheFooter from '~/components/common/TheFooter.vue'
export default {
  name: 'DefaultPage',
  components: { NavBar, TheFooter }
}
</script>

<style lang="postcss">
.hidden-scrollbar::-webkit-scrollbar {
  display: none;
}

.scrollbar:hover::-webkit-scrollbar-thumb {
  @apply bg-gray-800;
}
/* width */
.scrollbar::-webkit-scrollbar {
  width: 6px;
}

/* Track */
.scrollbar::-webkit-scrollbar-track {
  background: #fff;
}

/* Handle */
.scrollbar::-webkit-scrollbar-thumb {
  background: #888;
}
</style>
