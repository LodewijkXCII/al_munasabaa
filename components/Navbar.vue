<template>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <section>
    <modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">Offerte aanvragen</h3>
    </modal>
    <nav>
      <div class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8">
        <div class="relative flex items-center justify-between h-16">
          <div class="absolute inset-y-0 right-0 flex items-center sm:hidden">
            <!-- Mobile menu button-->
            <button
              class="inline-flex items-center justify-center p-2 rounded-md text-gray-400 hover:text-white  focus:outline-none focus:ring-2 focus:ring-inset focus:ring-white"
              aria-expanded="false"
            >
              <span class="sr-only">Open main menu</span>
              <!-- Icon when menu is closed. -->
              <!--
            Heroicon name: menu

            Menu open: "hidden", Menu closed: "block"
          -->
              <svg
                @click="menuOpen = !menuOpen"
                :class="menuOpen ? 'block' : 'hidden'"
                class="h-6 w-6"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M4 6h16M4 12h16M4 18h16"
                />
              </svg>
              <!-- Icon when menu is open. -->
              <!--
            Heroicon name: x

            Menu open: "block", Menu closed: "hidden"
          -->
              <svg
                @click="menuOpen = !menuOpen"
                :class="menuOpen ? 'hidden' : 'block'"
                class="h-6 w-6"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M6 18L18 6M6 6l12 12"
                />
              </svg>
            </button>
          </div>
          <div
            class="flex-1 flex sm:items-center justify-between items-stretch sm:justify-between"
          >
            <div class="flex-shrink-0 flex items-center">
              <nuxt-link to="/">
                <img
                  class="block lg:hidden h-14 p-4 w-auto"
                  src="~/assets/img/al_manusabaa_logo_small.png"
                  alt="Workflow"
                />
                <img
                  class="hidden lg:block h-14 m-4 w-auto"
                  src="~/assets/img/al_manusabaa_logo_small.png"
                  alt="Workflow"
                />
              </nuxt-link>
            </div>
            <div class="hidden sm:block sm:ml-6">
              <div class="flex space-x-4">
                <!-- Current: "bg-gray-900 text-white", Default: "text-gray-300 hover:bg-gray-700 hover:text-white" -->
                <nuxt-link to="/" class="gold px-3 py-2 text-sm font-medium">
                  Home
                </nuxt-link>

                <a
                  href="/#wiezijnwij"
                  class="text-gray-300 gold px-3 py-2 text-sm font-medium"
                >
                  Wie zijn wij?
                </a>
                <a
                  href="/#pakketten"
                  class="text-gray-300 gold px-3 py-2 text-sm font-medium"
                >
                  Pakketten en prijzen
                </a>
                <nuxt-link
                  to="/portfolio"
                  class="text-gray-300 gold px-3 py-2 text-sm font-medium"
                >
                  Portfolio
                </nuxt-link>
                <!-- <nuxt-link
                to="/zakelijk"
                class="text-gray-300 gold px-3 py-2 text-sm font-medium"
              >
                Zakelijk
              </nuxt-link>
              <nuxt-link
                to="/overige-diensten"
                class="text-gray-300 gold px-3 py-2 text-sm font-medium"
              >
                Overige diensten
              </nuxt-link> -->
                <nuxt-link
                  to="/contact"
                  class="text-gray-300 gold px-3 py-2 text-sm font-medium"
                >
                  Contact
                </nuxt-link>
                <a
                  @click="showModal = true"
                  class=" bg-gold hover:bg-gold-darker text-white py-3 px-6 rounded-lg hover:bg-gold-darker transition ease-in-out duration-300"
                >
                  Offerte aanvragen
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!--
    Mobile menu, toggle classes based on menu state.

    Menu open: "block", Menu closed: "hidden"
  -->
      <div
        class="sm:hidden"
        @click="menuOpen = !menuOpen"
        :class="menuOpen ? 'hidden' : 'block'"
      >
        <div class="px-2 pt-2 pb-3 space-y-1">
          <nuxt-link to="/" class="gold px-3 py-2 text-sm font-medium block">
            Home
          </nuxt-link>

          <a
            href="/#wiezijnwij"
            class="text-gray-300 gold px-3 py-2 text-sm font-medium block"
          >
            Wie zijn wij?
          </a>
          <a
            href="/#pakketten"
            class="text-gray-300 gold px-3 py-2 text-sm font-medium block"
          >
            Pakketten en prijzen
          </a>
          <nuxt-link
            to="/portfolio"
            class="text-gray-300 gold px-3 py-2 text-sm font-medium block"
          >
            Portfolio
          </nuxt-link>
          <!-- <nuxt-link
          to="/zakelijk"
          class="text-gray-300 gold px-3 py-2 text-sm font-medium block"
        >
          Zakelijk
        </nuxt-link> -->
          <!-- <nuxt-link
          to="/overige-diensten"
          class="text-gray-300 gold px-3 py-2 text-sm font-medium block"
        >
          Overige diensten
        </nuxt-link> -->
          <nuxt-link
            to="/contact"
            class="text-gray-300 gold px-3 py-2 text-sm font-medium block"
          >
            Contact
          </nuxt-link>
          <a
            @click="showModal = true"
            class="bg-gold hover:bg-gold-darker text-white py-3 px-6 rounded-lg hover:bg-gold-darker transition ease-in-out duration-300"
          >
            Offerte aanvragen
          </a>
        </div>
      </div>
    </nav>
  </section>
</template>

<script>
import Modal from '~/components/OfferteModal'
export default {
  components: {
    Modal
  },
  data() {
    return {
      menuOpen: false,
      showModal: false
    }
  }
}
</script>

<style lang="scss">
@import '../assets/scss/main.scss';

nav {
  background: rgba(29, 40, 58, 0.5);
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  padding: 0.5rem 0;
  .gold {
    color: white;
    &:hover {
      color: $gold-color;
      border-bottom: 1px solid $gold-color;
    }
  }
}
</style>
