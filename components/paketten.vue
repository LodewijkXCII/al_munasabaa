<template>
  <div class="bg-gray-700 relative col-span-4 lg:col-span-1 min-h-full">
    <div class="px-6 py-6 mb-4 text-center">
      <h3 class="text-2xl font-bold gold mb-4 uppercase">
        {{ titel }}
      </h3>
      <p class="text-lg text-weight-600 my-4">
        &euro; {{ prijs.toFixed(2) }} <span class="text-xs">/per persoon</span>
        <span class="text-xs block">(excl BTW)</span>
      </p>
    </div>
    <div class="px-6 mb-8">
      <div class="my-4">
        <p>Keuze uit {{ decoraties.length }} decoratielijnen</p>
      </div>
      <div class="my-4" v-if="dranken">
        <h4 class="gold font-bold text-lg">
          Drank gedurende het evenement:
        </h4>
        <p>{{ dranken }}</p>
      </div>
      <div class="my-4" v-if="voorHoofd">
        <h4 class="gold font-bold text-lg">Diner naar keuze:</h4>
        <p>{{ voorHoofd }}</p>
      </div>
      <div class="my-4" v-if="nagerecht">
        <h4 class="gold font-bold text-lg">Nagerecht:</h4>
        <p>{{ nagerecht }}</p>
      </div>
      <div class="my-4" v-if="dranken">
        <h4 class="gold font-bold text-lg">Dranken:</h4>
        <p>{{ dranken }}</p>
      </div>
    </div>
    <button
      class="w-full text-lg h-16 text-white font-extrabold bg-gold absolute -bottom-10"
    >
      <nuxt-link :to="`/pakketten/${slug}`">Bekijk details</nuxt-link>
    </button>
  </div>
</template>

<script>
export default {
  props: {
    description: String,
    gerechten: Array,
    prijs: Number,
    slug: String,
    titel: String,
    decoraties: Array,
    dranken: String,
    nagerecht: String,
    voorHoofd: String,
    vooraf: String
  },
  data() {
    return {
      pakketten: []
    }
  }
}
</script>

<style></style>
