<template>
  <footer
    class="flex flex-col md:flex-row w-full justify-between items-center mt-20 py-14 bg-slate-800 px-2 lg:px-20 xl:px-56"
  >
    <div class="w-full md:w-1/3">
      <img src="../../assets/img/coiled-dark.png" class="w-72" alt="" />
      <p class="-mt-3 text-sm text-gray-300">
        A clone ui from hybrid
        <a href="https://kumparan.com/" class="link">kumparan</a>
        and
        <a href="https://www.wired.com/" class="link">wired</a>
      </p>
      <hr class="my-2" />
      <a href="https://github.com/kamaludin21" class="link">Github</a>
      <span class="text-bold px-2">&bull;</span>
      <a href="https://twitter.com/KamalZyel" class="link">Twitter</a>
    </div>
    <div class="flex justify-end w-full md:w-2/3 space-x-8 text-sm">
      <div class="text-gray-300">
        <ul class="space-y-1">
          <li>Facebook</li>
          <li>Instagram</li>
          <li>Twitter</li>
          <li>Youtube</li>
          <li>LINE</li>
        </ul>
      </div>
      <div class="text-gray-300">
        <ul class="space-y-1">
          <li>Ketentuan &amp; Kebijakan Privasi</li>
          <li>Panduan Komunitas</li>
          <li>Pedoman Media Siber</li>
        </ul>
      </div>
      <div class="text-gray-300">
        <ul class="space-y-1">
          <li>Bantuan</li>
          <li>Iklan</li>
          <li>Karir</li>
        </ul>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "TheFooter",
};
</script>

<style lang="postcss" scoped>
.link {
  @apply text-gray-300;
}
</style>