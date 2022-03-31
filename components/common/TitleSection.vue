<template>
  <div class="flex w-full items-center justify-between pb-2">
    <p class="text-xl font-bold md:text-3xl capitalize">{{ title }}</p>
    <button class="flex items-center space-x-2 hover:text-teal-600">
      <span class="hidden font-medium md:block">Lihat lainnya</span>
      <arrow-right-icon size="1.5x" class="text-lg md:text-base" />
    </button>
  </div>
</template>

<script>
export default {
  name: 'TitleSection',
  props: {
    title: {
      type: String,
      default: 'Title'
    }
  }
}
</script>
