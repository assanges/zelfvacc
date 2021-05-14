<template>
  <div class="container">
    <script
      src="https://cdn.jsdelivr.net/gh/alpinejs/alpine@v2.x.x/dist/alpine.min.js"
      defer
    ></script>
    <div>
      <div class="hidden md:block">
        <section
          class="flex bg-landing-hero items-center justify-center"
          style="height: 460px"
        >
          <div class="text-center">
            <div
              class="text-xl tracking-wider text-gray-600 bg-gray-200 bg-opacity-50 space-y-2 py-2"
            >
              <h3>指揮中心自2021年4月21⽇起開放自費接種疫苗</h3>
              <h3>COVID-19疫苗哪裡打？疫苗副作用有哪些？</h3>
            </div>
            <h2
              class="my-8 font-black text-3xl tracking-wider text-white md:text-5xl"
            >
              自費接種疫苗資訊一次看
            </h2>

            <div class="flex justify-center mt-8">
              <NLink
                to="/jabs"
                class="px-8 py-2 text-lg font-medium text-white transition-colors duration-300 transform bg-indigo-500 rounded-full hover:bg-indigo-500"
                >了解更多
              </NLink>
            </div>
          </div>
        </section>
      </div>

      <!-- Leaflet -->
      <section class="bg-white">
        <div class="w-full md:max-w-5xl md:px-2 md:py-8 mx-auto text-center">
          <div id="map-wrap" style="rounded-lg ">
            <client-only>
              <VMap />
            </client-only>
          </div>
        </div>
      </section>

      <section class="bg-white">
        <div class="max-w-5xl px-6 py-16 mx-auto">
          <h2 class="text-3xl font-semibold text-gray-800">
            自費接種 COVID-19 疫苗
          </h2>

          <div class="grid gap-8 my-12 md:grid-cols-2 lg:grid-cols-3">
            <div
              v-for="(item, index) in info_before_jab"
              :key="index"
              class="px-6 py-8 overflow-hidden bg-gray-50 rounded-md shadow-md"
            >
              <div class="flex-shrink-0">
                <div
                  class="flex items-center mx-auto justify-center h-12 w-12 rounded-full bg-pink-500 text-white"
                >
                  <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-8 w-8"
                    viewBox="0 0 20 20"
                    fill="currentColor"
                  >
                    <path fill-rule="evenodd" :d="item.d" clip-rule="evenodd" />
                  </svg>
                </div>
              </div>
              <h2 class="text-xl font-medium text-gray-800 pt-4">
                {{ item.title }}
              </h2>
              <p class="max-w-md mt-4 text-left text-gray-600">
                {{ item.description }}
              </p>
            </div>
          </div>
          <div class="md:flex md:justify-between">
            <h2 class="text-lg font-semibold text-gray-800">
              對自費接種 COVID-19 疫苗還有疑問？
            </h2>
            <a
              href="https://www.cdc.gov.tw/File/Get/ko-N8FqW1XYxWt4-aVBTww"
              class="block mt-6 text-indigo-700 underline md:mt-0"
            >
              自費接種問答輯<Extlink />
            </a>
          </div>
        </div>
      </section>

      <section class="bg-grey-100">
        <div class="max-w-5xl px-6 py-8 mx-auto text-center">
          <h2 class="text-3xl font-semibold text-gray-800">
            COVID-19疫苗接種後注意事項
          </h2>

          <img
            class="object-cover object-center w-full mt-8 rounded-md shadow h-96"
            alt="covid-19 vaccine (@hakannural)"
            src="https://images.unsplash.com/photo-1608243499644-c55bd9f2b837?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=872&q=80"
          />
          <div
            class="flex flex-wrap lg:max-w-5xl sm:mx-auto mt-16 text-left text-lg"
          >
            <div
              v-for="(item, index) in info_after_jab"
              :key="index"
              class="p-2 sm:w-1/2 w-full"
            >
              <div
                class="bg-gray-100 rounded shadow flex p-4 h-full items-center"
              >
                <svg
                  fill="none"
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="3"
                  class="text-green-600 w-12 h-12 flex-shrink-0 mr-7"
                  viewBox="0 0 24 24"
                >
                  <path d="M22 11.08V12a10 10 0 11-5.93-9.14"></path>
                  <path d="M22 4L12 14.01l-3-3"></path>
                </svg>
                <!-- eslint-disable-next-line vue/no-v-html -->
                <p v-html="item.point"></p>
              </div>
            </div>
          </div>
          <p class="max-w-2xl mx-auto mt-8 text-gray-600">
            如有相關疑問可撥打免付費防疫專線1922（或0800-001922）洽詢。
          </p>
        </div>
      </section>
    </div>
  </div>
</template>

<script language="ts">
export default {
  data() {
    return {
      info_before_jab: [
        {
          title: '開放對象',
          description:
            '⑴ 以商務、工作、留學或就醫等人道因素為原則，不限國籍身分別； ⑵ 持有有效居留證件之外籍人士。',
          d:
            'M13.586 3.586a2 2 0 112.828 2.828l-.793.793-2.828-2.828.793-.793zM11.379 5.793L3 14.172V17h2.828l8.38-8.379-2.83-2.828z',
        },
        {
          title: '所需費用',
          description:
            '自費接種者需自付醫院收取之掛號費、診察費、注射費等；免收疫苗費用。實際費用請洽詢各醫院。',
          d:
            'M4 4a2 2 0 00-2 2v4a2 2 0 002 2V6h10a2 2 0 00-2-2H4zm2 6a2 2 0 012-2h8a2 2 0 012 2v4a2 2 0 01-2 2H8a2 2 0 01-2-2v-4zm6 4a2 2 0 100-4 2 2 0 000 4z',
        },
        {
          title: '異地接種',
          description:
            '⺠眾可依需求，選定不同旅醫合約醫院之旅遊醫學門診，接種前後兩劑之COVID-19疫苗。',
          d:
            'M4 4a2 2 0 012-2h8a2 2 0 012 2v12a1 1 0 110 2h-3a1 1 0 01-1-1v-2a1 1 0 00-1-1H9a1 1 0 00-1 1v2a1 1 0 01-1 1H4a1 1 0 110-2V4zm3 1h2v2H7V5zm2 4H7v2h2V9zm2-4h2v2h-2V5zm2 4h-2v2h2V9z',
        },
      ],
      info_after_jab: [
        {
          point:
            '接種後應於接種單位或附近<span class="text-yellow-600 font-bold">休息至少30分鐘</span>再離開',
        },
        {
          point:
            '使用抗血小板或抗凝血藥物或凝血功能異常者，施打後於注射部位<span class="text-yellow-600 font-bold">加壓至少2分鐘</span>，並觀察是否仍有出血或血腫情形',
        },
        {
          point:
            '接種後可能發生<span class="text-yellow-600 font-bold">接種部位疼痛、紅腫</span >，其他可能反應包含<span class="text-yellow-600 font-bold">疲倦、頭痛、肌肉痠痛、體溫升高、畏寒、關節痛及噁心</span>，症狀隨年齡層增加而減少，通常輕微並於數天內消失',
        },
        {
          point:
            '接種後<span class="text-yellow-600 font-bold">可能有發燒反應（≥38℃）</span>，約48小時可緩解，如<span class="text-red-600 font-bold">持續發燒超過48小時、嚴重過敏反應如呼吸困難、氣喘、眩暈、心跳加速、全身紅疹</span>等不適症狀，應<span class="bg-red-600 mx-0.5 px-1 tracking-wider text-white font-bold">儘速就醫</span>，並告知醫師曾接種疫苗，同時請醫師通報',
        },
        {
          point:
            '接種後若14天內出現<span class="text-red-600 font-bold">呼吸困難、胸痛或腹痛、四肢腫脹或冰冷、嚴重頭痛或疼痛加劇、視力模糊、持續出血、皮膚出現自發性瘀靑、紫斑</span>等症狀，應<span class="bg-red-600 mx-0.5 px-1 tracking-wider text-white font-bold">立即就醫</span>',
        },
        { point: '其他中央流行疫情指揮中心公告之事項' },
      ],
    }
  },
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.bg-landing-hero {
  background-image: url('https://images.unsplash.com/photo-1612537786199-1c202c6dcfd2?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1267&q=80');
  background-position: bottom center;
  background-repeat: fixed;
  background-size: cover;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
