<template>
  <div class="container mx-auto md:py-16">
    <div class="max-w-5xl px-6 py-8 mx-auto text-center">
      <h2 class="text-4xl font-semibold text-gray-800 pb-8">常見問題 FAQ</h2>
      <div class="md:flex md:justify-between">
        <p class="text-sm text-gray-500">
          摘錄自
          <a class="underline" href="http://at.cdc.tw/B42hEv/"
            >http://at.cdc.tw/B42hEv</a
          >
        </p>
      </div>
      <div class="flex flex-wrap lg:max-w-3xl sm:mx-auto mt-16 text-left">
        <div
          v-for="(faq, index) in faq_excerpt"
          :key="index"
          class="font-medium text-gray-900 flex-col"
        >
          <p class="text-green-700 pb-4" :v-html="faq.question">
            Q: {{ faq.question }}
          </p>
          <p class="pb-12 tracking-wide" :v-html="faq.answer">
            A: {{ faq.answer }}
          </p>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      faq_excerpt: [
        {
          question:
            '國內初期自國外採購將用於國內接種的COVID-19疫苗有哪些種類？',
          answer:
            '現階段採購之COVID-19疫苗，依據其製造原理分別有mRNA疫苗以及腺病毒載體疫苗兩大類。其中mRNA疫苗將可能有Pfizer/BioNTech (BNT162b2)及Moderna(mRNA-1273)等，腺病毒載體疫苗則將有AstraZeneca (AZ1222)等。',
        },
        {
          question: 'COVID-19疫苗的作用原理是什麼？',
          answer:
            '目前核准使用的COVID-19疫苗，包括mRNA疫苗與腺病毒載體疫苗兩種。mRNA疫苗含有一段可轉譯成SARS-CoV-2病毒棘蛋白（病毒結構蛋白之一，為目前SARS-CoV-2疫苗選定之疫苗抗原）的mRNA，接種後在人體細胞質內製造棘蛋白此疫苗抗原並釋出細胞外，進而刺激免疫系統產生對抗SARS-CoV-2棘蛋白的細胞免疫力與體液免疫力。病毒載體疫苗則是利用攜帶有SARS-CoV-2 棘蛋白核酸序列（DNA核酸序列）的腺病毒，接種後在人體細胞內製造SARS-CoV-2棘蛋白此疫苗抗原並自人體細胞釋出，誘發人體免疫系統產生保護力對抗病毒入侵。',
        },
        {
          question:
            '目前我國疫苗接種計畫將使用之AstraZeneca      COVID-19疫苗內含哪些成分?有佐劑或防腐劑嗎? ',
          answer:
            '目前我國使用的AstraZeneca COVID-19疫苗，根據其仿單記載，每0.5mL內含成分包括不低於 2.5 × 10的8次方個感染單位 （Inf.U）之黑猩猩腺病毒（ChAdOx1）顆粒、鈉（含量低於 1 mmol）、乙醇2mg與賦形劑，並不含佐劑與防腐劑。',
        },
        {
          question: '接種mRNA COVID-19疫苗會改變我的DNA? ',
          answer:
            '否。COVID-19 mRNA疫苗不會以任何方式改變您的DNA或與您的DNA產生交互作用。mRNA疫苗作用機轉是教導人體細胞自行產出SARS-CoV-2病毒蛋白質片段（疫苗抗原），進而誘發體內產生免疫反應。疫苗中的mRNA永遠不會進入細胞核（人體DNA存在的地方）。非複製型腺病毒載體疫苗是利用修飾後的腺病毒做為載體，病毒的DNA嵌入可表現SARS-CoV-2病毒棘蛋白的基因，此腺病毒不具人體內複製力、亦無人體致病性。接種後進入人體宿主細胞內表達疫苗抗原（SARS-CoV-2棘蛋白），進而誘導宿主對該疫苗抗原蛋白產生免疫反應。由病毒載體所攜帶的基因片段並不會嵌入人體的DNA。',
        },
        {
          question: '不同廠牌的COVID-19疫苗，效果是一樣的嗎?',
          answer:
            '目前核准使用的COVID-19疫苗，均經過衛生主管機關審查其效果與安全性符合標準，可以有效預防COVID-19有症狀感染、重症或死亡。',
        },
        {
          question: 'COVID-19疫苗可以預防流感或其他疾病嗎?',
          answer:
            '不行。COVID-19疫苗僅可預防COVID-19感染，無法預防流感或其他疾病。',
        },
        {
          question: '接種COVID-19疫苗要帶什麼證件?',
          answer:
            '公費COVID-19疫苗實施對象接種所需證件，依其所屬類別，略有差異，詳請參閱「110年COVID-19疫苗接種計畫」之「附件6 COVID-19疫苗接種對象接種所需證件及費用」。',
        },
        {
          question: '接種COVID-19疫苗後仍可能會感染COVID-19嗎？',
          answer:
            '疫苗保護力並非100%，接種疫苗後，仍有少數機會會罹患COVID-19。因此即使完成COVID-19疫苗接種，仍應遵守防疫新生活原則，勤洗手、佩戴口罩、保持社交距離，以降低感染風險。',
        },
        {
          question: '接種COVID-19疫苗，是否可降低將疾病傳染給他人的機率?',
          answer:
            '目前尚無足夠證據顯示，接種COVID-19疫苗後若仍感染，可降低病毒排出或傳染給他人的機率。',
        },
        {
          question: '根據臨床試驗結果，COVID-19疫苗保護力有多少?',
          answer:
            '目前國際間緊急授權使用的COVID-19疫苗包括AstraZeneca(AZ)、Pfizer-BioNTech、Moderna與Janssen等廠牌，在完整接種兩劑(或一劑)後，對預防PCR確診SARS-CoV-2（疫苗株或D614G株）之有症狀感染，其保護力約有六至九成。',
        },
        {
          question: '接種COVID-19疫苗後，我仍需要佩戴口罩、保持社交距離嗎？',
          answer:
            '疫苗保護力並非100%，且目前接種疫苗的人數仍為少數。故在疫苗涵蓋率仍不高的情況下，為預防疾病的發生、保護易感族群，建議即使完成COVID-19疫苗接種，仍應遵守防疫新生活原則，勤洗手、佩戴口罩、保持社交距離。因目前國際疫情仍嚴峻，且疫苗涵蓋率尚不足，故自國外入境者仍須依照中央流行指揮中心規定進行入境居家檢疫及自主健康管理。',
        },
      ],
    }
  },
}
</script>
