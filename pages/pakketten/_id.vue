<template>
  <section>
    <div class="">
      <img
        v-if="pakket.Afbeelding"
        :src="pakket.Afbeelding.url"
        alt="Romantic Blue overview"
        class="top-img-half"
      />
      <div class="img-full container mx-auto half-full text-center">
        <h1 class="title lg:text-7xl md:text-6xl text-4xl"></h1>
      </div>
    </div>
    <div class="container mx-auto grid grid-cols-6  my-10">
      <div class="col-span-4 col-start-2 justify-center px-4">
        <h1
          class="gold py-4 text-center font-bold uppercase lg:text-4xl text-2xl"
        >
          {{ pakket.Titel }}
        </h1>

        <p>{{ pakket.Omschrijving }}</p>
        <ul class="list-none list-inside	 ml-10 mt-2 pt-3">
          <li v-if="pakket.Dranken" class="py-1 pakketList ">
            {{ pakket.Dranken }}
          </li>
          <li v-if="pakket.Voorafje" class="py-1 pakketList ">
            {{ pakket.Voorafje }}
          </li>
          <li v-if="pakket.VoorHoofdgerecht" class="py-1 pakketList ">
            {{ pakket.VoorHoofdgerecht }}
          </li>
          <li v-if="pakket.Nagerecht" class="py-1 pakketList ">
            {{ pakket.Nagerecht }}
          </li>
        </ul>
        <div class="mt-8">
          <h3 class="text-2xl font-bold gold mb-1 uppercase">
            Prijs per persoon
          </h3>
          <p class="text-lg text-weight-600">
            &euro; {{ pakket.Prijs }}
            <span class="text-xs">(exlusief BTW)</span>
          </p>
        </div>
      </div>
      <!-- <div class="col-span-2" v-if="pakket.Afbeelding">
        <img
          :src="pakket.Afbeelding.url"
          alt="Romantic Blue overview"
          class="lg:block hidden"
        />
      </div> -->
    </div>
    <div class="container mx-auto my-10">
      <h2
        class="gold py-4 text-center font-bold uppercase lg:text-4xl text-2xl"
      >
        Keuze uit de volgende decoratie lijnen:
      </h2>

      <div class="container mx-auto grid md:grid-cols-4 p-8 gap-8">
        <div
          class="bg-gray-700"
          v-for="decoratie in pakket.Decoraties"
          :key="decoratie._id"
        >
          <img :src="url" alt="" class="w-full h-48 sm:h-56 object-cover" />

          <div
            class="lg:text-2xl text-xl font-bold gold uppercase text-center mx-auto my-8"
          >
            {{ decoratie.titel }}
          </div>
        </div>
      </div>
    </div>
    <div class="container mx-auto my-10">
      <h2
        class="gold py-4 text-center font-bold uppercase lg:text-4xl text-2xl"
      >
        Keuze uit de volgende gerechten:
      </h2>
      <div
        class="container mx-auto grid md:grid-cols-4 p-8 gap-8"
        v-for="(gang, name) in gerechten"
        :key="gang.id"
      >
        <h4
          class="gold py-4 text-center font-bold uppercase text-2xl mx-auto self-center"
        >
          {{ name }}:
        </h4>
        <div class="bg-gray-700" v-for="gerecht in gang" :key="gerecht._id">
          <img
            src="https://picsum.photos/400/600/?random"
            alt=""
            class="w-full h-48 sm:h-56 object-cover"
          />

          <div
            class="lg:text-2xl text-xl font-bold gold uppercase text-center mx-auto my-8"
          >
            {{ gerecht.titel }}
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import _ from 'lodash'

export default {
  data() {
    return {
      pakket: {},
      gerechten: []
    }
  },
  async mounted() {
    const params = this.$route.params.id

    const URL = 'https://al-munasabaa.herokuapp.com/pakettens'
    try {
      const data = await this.$axios.$get(`${URL}?slug=${params}`)
      console.log(data[0])
      this.pakket = data[0]
      const gerechten = data.paketten[0].gerechten
      this.gerechten = _.groupBy(gerechten, 'course')
    } catch (error) {
      console.error(error)
    }
  }
}
</script>

<style lang="scss">
@import '~/assets/scss/main.scss';

.pakketList::before {
  content: '\2022';
  color: $gold-color;
  font-weight: bold;
  display: inline-block;
  width: 1em;
  margin-left: -1em;
}
</style>
