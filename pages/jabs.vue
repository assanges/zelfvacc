<template>
  <div class="container mx-auto">
    <section class="bg-white">
      <div class="max-w-5xl px-6 py-16 mx-auto">
        <h2 class="text-4xl font-semibold py-6 text-gray-800 leading-relaxed">
          疫苗簡介 Jabs
        </h2>
        <div class="md:flex md:justify-between mb-8 mx-2">
          <h5 class="text-sm text-gray-500">
            摘錄自
            <a class="underline" href="http://at.cdc.tw/J39G7B"
              >http://at.cdc.tw/J39G7B</a
            >
          </h5>
          <h5 class="text-sm text-gray-400">最後整理：2021-05-20</h5>
        </div>
        <!-- component -->
        <div id="app">
          <div
            v-for="jab in Impfstoff"
            :key="jab.key"
            class="max-w-3xl rounded-lg mb-8 border border-gray-200 shadow-lg"
          >
            <div
              class="
                flex flex-row
                justify-between
                p-6
                bg-white
                border-b border-gray-200
              "
            >
              <h3 class="text-2xl font-semibold text-gray-800 leading-relaxed">
                {{ jab.name }}
              </h3>
            </div>
            <div class="px-6 py-5 bg-gray-50 text-left">
              <div v-for="(overview, index) in jab.overview" :key="index">
                <div>
                  <h5 class="my-2 text-xl font-normal text-gray-500">
                    <!-- {{ jabSubtitle.title }} -->
                  </h5>
                  <p
                    class="mb-4 font-medium text-gray-800"
                    v-html="overview"
                  ></p>
                </div>
              </div>
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
      Impfstoff: [
        {
          key: 'aZ',
          name: 'AstraZeneca COVID-19 疫苗',
          overview: [
            'AstraZeneca之COVID-19疫苗是含有SARS-CoV-2病毒棘蛋白(S-protein)基因之非複製型腺病毒載體之疫苗，用於預防COVID-19。本疫苗已通過WHO、歐盟等其他先進國家及我國緊急授權使用。',
            '目前依據疫苗仿單之適用接種年齡為18歲以上，接種劑量為0.5 mL。\n接種劑次為2劑，目前依世界衛生組織(WHO)建議接種間隔為8至12週；依我國衛生福利部傳染病防治諮詢會預防接種組(ACIP)建議為至少8週以上。\n接種途徑為肌肉注射。',
            '對於疫苗成分有嚴重過敏反應史，或對於先前接種之疫苗劑次發生嚴重過敏反應者不予接種。',
            '本疫苗不含可複製之SARS-CoV-2病毒顆粒，不會因為接種本疫苗而罹患COVID-19。完成2劑接種可預防63%有症狀感染之風險，另依臨床試驗資料分析，當接種間隔12週且完成2劑接種，保護力約81% (60% ~ 91%)。',
            '本疫苗成分尚包含L-Histidine、L-Histidine hydrochloride monohydrate、氯化鎂、聚山梨醇酯80 (Polysorbate 80)、乙醇、蔗糖、氯化鈉、乙二胺四乙酸二鈉(EDTA-2Na)。',
          ],
        },
        {
          key: 'pBNT',
          name: 'Pfizer-BioNTech  COVID-19 疫苗',
          overview: [
            'Pfizer-BioNTech之COVID-19疫苗是含有SARS-CoV-2病毒棘蛋白(S protein)之mRNA疫苗，用於預防COVID-19，本疫苗目前已通過WHO、歐盟、美國等先進國家緊急授權使用。',
            '目前依據疫苗仿單之適用接種年齡為18歲以上，接種劑量為0.5 mL。接種劑次為2劑，目前依國際指引及衛生福利部傳染病防治諮詢會預防接種組(ACIP)建議接種間隔為至少28 天。接種途徑為肌肉注射。',
            '本疫苗不含可複製之SARS-CoV-2病毒顆粒，不會因為接種本疫苗而罹患COVID-19。依據目前臨床試驗結果資料顯本疫苗接種完成2劑接種7天後之保護力約95%(90.3% ~ 97.6%)，疫苗的保護效果需視接種對象的年齡或身體狀況而異。',
            '對於疫苗成分有嚴重過敏反應史，或對於先前接種之疫苗劑次發生嚴重過敏反應者不予接種。',
            '本疫苗成分尚包含脂類｛（4-羥丁基）氮雜二基）雙（己烷-6,1-二基）雙（2-己基癸酸酯）、2 [（聚乙二醇）-2000] N，N-二十四烷基乙醯胺、1，2-二硬脂基-sn-甘油-3-磷酸膽鹼｝和膽固醇、氯化鉀、磷酸二氫鉀、氯化鈉、磷酸氫二鈉二水合物和蔗糖。',
          ],
        },
        {
          key: 'moderna',
          name: 'Moderna COVID-19 疫苗',
          overview: [
            'Moderna之COVID-19疫苗是SARS-CoV-2病毒棘蛋白(S protein)之mRNA疫苗。本疫苗目前已通過美國、歐盟等先進國家緊急授權使用。',

            '目前依據疫苗仿單之適用接種年齡為18歲以上，接種劑量為0.5 mL。接種劑次為2劑，目前依國際指引及衛生福利部傳染病防治諮詢會預防接種組(ACIP)建議接種間隔為至少28 天。接種途徑為肌肉注射。',

            '本疫苗不含可複製之SARS-CoV-2病毒顆粒，不會因為接種本疫苗而罹患COVID-19。接種2劑可預防94%有症狀之感染。',
            '對於疫苗成分有嚴重過敏反應史，或對於先前接種之疫苗劑次發生嚴重過敏反應者不予接種。',
            '本疫苗成分尚包含脂類｛SM-102、聚乙二醇[PEG] 2000 二肉豆蔻醯基甘油 [DMG]、膽固醇、1，2-二硬脂醯基-sn-甘油-3-磷酸膽鹼 (DSPC)｝、氨丁三醇、鹽酸氨丁三醇、乙酸、乙酸鈉和蔗糖。',
          ],
        },
        // {
        //   jabSubtitle: [
        //     { key: 'overview', title: '疫苗概述' },
        //     { key: 'dosages', title: '接種劑量及間隔' },
        //     { key: 'effetectiveness', title: '安全性及保護效果' },
        //     { key: 'contraindications', title: '接種禁忌' },
        //     { key: 'precautionsBefore', title: '接種注意事項' },
        //     { key: 'precautionsAfter', title: '接種後注意事項' },
        //     { key: 'sideEffects', title: '接種後可能發生之反應及因應措施' },
        //     { key: 'inactiveIngredients', title: '疫苗其他成分' },
        //   ],
        // },
      ],
    }
  },
}
</script>
