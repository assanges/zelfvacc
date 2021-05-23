<template>
  <div class="mx-auto container flex flex-col items-center justify-center">
    <div class="text-black flex flex-col md:items-center">
      <h1 class="text-2xl font-bold leading-relaxed">Zelfvacc 自費疫苗地圖</h1>
      <div class="md:flex place-items-center mt-5 text-base leading-tight">
        <ul id="footer" class="md:flex items-center md:space-x-3">
          <li
            v-for="(item, index) in footer_sitemap"
            :key="index"
            class="cursor-pointer pt-4 lg:py-0"
          >
            <NLink :to="item.route"> {{ item.title }}</NLink>
          </li>
        </ul>
      </div>
      <div
        class="
          md:flex
          my-6
          text-sm text-gray-500
          leading-tight
          place-items-center
          md:space-x-6
        "
      >
        <a
          v-for="(item, index) in footer_externals"
          :key="index"
          :href="item.href"
          target="_blank"
          rel="noopener noreferrer"
          >{{ item.title }}</a
        >
      </div>
      <div class="text-sm text-gray-500 leading-tight mx-2">
        <p>
          本站資料係整理自中華民國衛生福利部疾病管制署網站依<a
            class="underline px-0.5"
            target="_blank"
            rel="noreferrer noopener"
            href="http://at.cdc.tw/4s60aK"
            >政府網站資料開放宣告</a
          >
          <Extlink />構成。
        </p>
        <p>
          Data are retrieved from the Taiwan Centers for Disease Control under
          <a
            class="underline px-0.5"
            target="_blank"
            rel="noreferrer noopener"
            href="http://at.cdc.tw/a57ow2"
            >Government Website Open Information Announcement</a
          >
          <Extlink />.
        </p>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      footer_sitemap: [
        { title: 'Home', route: '/' },
        { title: 'Locations', route: '/location' },
        { title: 'Jabs', route: '/jabs' },
        { title: 'FAQs', route: '/faq' },
        { title: 'Disclaimer', route: '/disclaimer' },
      ],
      footer_externals: [
        {
          title: 'View on Github',
          href: 'https://github.com/assanges/zelfvacc/',
        },
        { title: 'OpenStreetMap × Wikidata', href: '#' },
        { title: 'COSCUP 2021', href: 'https://coscup.org/2021/' },
      ],
    }
  },
}
</script>
