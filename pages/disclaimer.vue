<template>
  <div class="container mx-auto">
    <section class="bg-white">
      <div class="max-w-5xl px-6 py-16 mx-auto">
        <h2 class="text-3xl font-semibold text-gray-800 leading-relaxed">
          免責事項 DISCLAIMER
        </h2>
        <img
          class="object-cover object-center w-full max-w-3xl mt-8 rounded-md shadow h-72"
          alt="National Kaohsiung Center for the Arts (@andywang02021)"
          src="https://images.unsplash.com/photo-1556309802-a237781b678f?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1050&q=80"
        />
        <div class="max-w-3xl py-16 mx-auto">
          <div
            class="md:flex md:flex-col place-items-center text-left my-6 text-sm md:space-x-6"
          >
            <div>
              <ul class="space-y-6 text-gray-700 tracking-wide">
                <!-- eslint-disable vue/no-v-html -->
                <li
                  v-for="(item, index) in disclaimer_text"
                  :key="index"
                  class="pt-4 lg:py-0 leading-relaxed"
                  v-html="item.text"
                ></li>
                <!-- eslint-disable-end -->
              </ul>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      disclaimer_text: [
        {
          text:
            '<span class="text-lg tracking-wider">使用本網站前請您先閱讀下列免責事項。當您使用本網站服務時，即視同您同意下列事項。若不同意，請勿使用本網站及相關服務。</span>',
        },
        {
          text:
            '<span class="text-pink-600 font-bold">本網站不提供醫療建議</span>。本網站所提供的資訊僅供參考之用，並不能代替醫師之專業意見、診斷、或治療；以及未必適用於任何情境。',
        },
        {
          text:
            '<span class="text-pink-600 font-bold">如有任何健康或醫療疑問應即就醫</span>，並向醫師諮詢專業意見或尋求治療建議。請勿因閲覧本網站內容而忽視專業醫療建議或延誤就醫。',
        },
        {
          text:
            '本網站致力於確保刊載內容之正確性，惟不會就其準確性、可用性或時效作出任何保證。本網站亦不會就任何因提供的資訊而引起的損失或損害承擔任何責任。',
        },
        { text: '本網站上之內容及連結有可能會在未經預告下増修或刪改。' },
        { text: '本頁所揭示之免責事項有可能會在未經預告下進行修訂。' },
      ],
    }
  },
}
</script>
