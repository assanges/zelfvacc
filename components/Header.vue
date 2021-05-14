<template>
  <div>
    <header class="bg-green-400">
      <nav
        class="px-6 py-4 mx-auto md:flex md:max-w-4xl md:justify-between md:items-center"
      >
        <div class="flex items-center justify-between">
          <NLink
            to="/"
            class="text-xl font-bold text-white transition-colors duration-300 transform md:text-3xl"
            >Zelfvacc
          </NLink>

          <!-- Mobile menu button -->
          <div class="flex md:hidden" @click="isOpen = !isOpen">
            <button
              type="button"
              class="text-white focus:outline-none"
              aria-label="Menu"
            >
              <svg viewBox="0 0 24 24" class="w-6 h-6 fill-current">
                <path
                  fill-rule="evenodd"
                  d="M4 5h16a1 1 0 0 1 0 2H4a1 1 0 1 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2zm0 6h16a1 1 0 0 1 0 2H4a1 1 0 0 1 0-2z"
                ></path>
              </svg>
            </button>
          </div>
        </div>

        <!-- Mobile Menu open: "block", Menu closed: "hidden" -->
        <div
          :class="isOpen ? 'flex' : 'hidden'"
          class="flex-col mt-4 space-y-4 md:flex md:space-y-0 md:flex-row md:items-center md:space-x-10 md:mt-0"
        >
          <NLink
            v-for="(link, index) in header"
            :key="index"
            class="text-sm font-medium text-gray-900 transition-colors duration-300 transform hover:text-indigo-700"
            :to="link.route"
            >{{ link.title }}
          </NLink>

          <a
            class="px-4 py-1 text-sm font-medium text-center text-white transition-colors duration-300 transform bg-green-800 rounded-full hover:bg-indigo-600 hover:text-white"
            href="http://at.cdc.tw/o65opy"
            >TWCDC 疾管署 <Extlink />
          </a>
        </div>
      </nav>
    </header>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      isOpen: false,
      header: [
        { title: '院所列表', route: '/location' },
        { title: '疫苗簡介', route: '/jabs' },
        { title: '疫苗Q&A', route: '/faq' },
        { title: 'i18n', route: '' },
      ],
    }
  },
}
</script>
