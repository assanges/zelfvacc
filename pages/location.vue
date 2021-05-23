<template>
  <div id="app" class="container mx-auto">
    <section class="bg-white">
      <div class="max-w-5xl px-6 py-16 mx-auto">
        <h2 class="text-4xl font-semibold py-6 text-gray-800 leading-relaxed">
          接種院所 Locations
        </h2>
        <div class="md:flex md:justify-between mb-8 mx-2">
          <h5 class="text-sm text-gray-400">最後整理：2021-05-20</h5>
        </div>

        <!-- on-hold alert start -->
        <div
          class="bg-yellow-100 border border-yellow-500 px-4 py-3"
          role="alert"
        >
          <div class="text-center font-semibold">
            因COVID-19疫苗配送數量限制，目前自費COVID-19疫苗接種服務已暫停，各院所將視疫苗後續配送情形再行開放。
          </div>
        </div>
        <!-- on-hold alert end -->

        <div class="grid gap-5 my-12 md:grid-cols-2 lg:grid-cols-3">
          <div
            v-for="ort in krankenhaus"
            :key="ort.id"
            class="max-w-4xl rounded-lg p-6 mb-4 border border-gray-200 shadow-md"
          >
            <!-- eslint-disable vue/no-v-html -->
            <h5
              class="my-2 text-2xl font-normal tracking-wide text-blue-900"
              v-html="ort.hospital"
            ></h5>
            <p class="my-2" v-html="ort.opd"></p>
            <p class="my-3">
              <span
                class="px-3 py-px text-sm font-semibold tracking-wider text-indigo-700 uppercase rounded-full border-2 border-indigo-600 hover:border-blue-800 hover:text-blue-800"
                v-html="ort.city"
              >
              </span>
            </p>
            <div class="flex flex-col font-medium text-gray-800 my-6">
              <p class="mb-2" v-html="ort.address"></p>
              <p class="mb-2" v-html="ort.tel"></p>
            </div>
            <a
              class="my-2 px-6 py-2 rounded-full font-semibold tracking-wider bg-pink-500 text-sm text-white outline-none focus:outline-none hover:shadow-sm hover:bg-pink-600 transition duration-200 ease-in-out"
              :href="ort.website"
              >査詢預約情況</a
            >
            <!-- eslint-enable -->
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import axios from 'axios'

export default Vue.extend({
  el: '#app',
  data() {
    return {
      krankenhaus: null,
    }
  },
  mounted() {
    const krankenhaeuser =
      'https://gist.githubusercontent.com/assanges/e0b375cc84c2c19b66e939763bef1447/raw/f91ebeeaaa9c6e310d02945a16c10814c192a2f1/zelfvacc-opd.json'
    axios
      .get(krankenhaeuser)
      .then((response) => (this.krankenhaus = response.data))
  },
})
</script>
