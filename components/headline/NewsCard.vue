<template>
  <div
    class="bg-gray-600 bg-cover bg-center bg-no-repeat"
    :style="{ backgroundImage: `url('${thumbnailImage}')` }"
  >
    <div class="flex h-full w-full flex-row items-end">
      <div class="flex w-full flex-col bg-gradient-to-t from-black p-3 text-gray-200">
        <slot></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'NewsCard',
  props: {
    thumbnailImage: {
      type: String,
      default: '0'
    }
  }
}
</script>
