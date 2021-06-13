<template>
  <section>
    <div>
      <img
        src="@/assets/img/flower_gold_table.jpg"
        alt="Romantic Blue overview"
        class="top-img-half"
      />
      <div class="img-full container half-full mx-auto">
        <h1 class="title lg:text-7xl md:text-6xl text-4xl text-center gold">
          Portfolio
        </h1>
      </div>
    </div>

    <div class="py-20 px-8 container mx-auto" id="gerechten">
      <div class="col-span-4 my-auto">
        <h2 class="gold text-4xl font-bold text-center mb-6">Gerechten</h2>
        <h3 class="gold text-xl font-bold text-center mb-3">
          Moderne gerechten, traditionele kwaliteit.
        </h3>
        <p class="my-4">
          Als vanzelfsprekend werken wij met enkel verse en pure ingrediënten
          welke wij daags voor uw gelegenheid inkopen bij onze vaste
          distributeurs. Met grote zorg en met behoud van de pure smaken worden
          deze door onze koks op traditionele wijze verwerkt tot een heerlijk
          smakenpallet. Wij hebben onze traditionele gerechten qua opmaak in een
          modern jasje voor u gestoken en bieden naast traditionele gerechten
          een scala aan meer eigentijdse variaties. Laat u verrassen door de
          overweldigende smaken en de prachtige opmaak van onze gerechten.
        </p>

        <div class="grid lg:grid-cols-4 gap-4 my-8">
          <div class="">
            <div
              class="text-2xl font-bold gold uppercase text-center mx-auto my-8"
              @click="show == 1"
            >
              <h3>Voor- Hoofdgerechten</h3>
            </div>
          </div>
          <div
            class="bg-gray-700"
            v-for="gerecht in gerechten.Voor_hoofd"
            :key="gerecht.id"
          >
            <img
              v-if="gerecht.Afbeelding"
              :src="gerecht.Afbeelding.url"
              :alt="gerecht.caption"
              class="w-full h-48 sm:h-56 object-cover"
            />
            <div
              class="text-2xl font-bold gold uppercase text-center mx-auto my-8"
            >
              {{ gerecht.Titel }}
            </div>
          </div>
        </div>
        <div class="grid lg:grid-cols-4 gap-4 my-8">
          <div class="">
            <div
              class="text-2xl font-bold gold uppercase text-center mx-auto my-8"
              @click="show == 1"
            >
              <h3>Dessert</h3>
            </div>
          </div>
          <div
            class="bg-gray-700"
            v-for="gerecht in gerechten.Dessert"
            :key="gerecht.id"
          >
            <img
              v-if="gerecht.Afbeelding"
              :src="gerecht.Afbeelding.url"
              :alt="gerecht.caption"
              class="w-full h-48 sm:h-56 object-cover"
            />
            <div
              class="text-2xl font-bold gold uppercase text-center mx-auto my-8"
            >
              {{ gerecht.Titel }}
            </div>
          </div>
        </div>
        <div class="grid lg:grid-cols-4 gap-4 my-8">
          <div class="">
            <div
              class="text-2xl font-bold gold uppercase text-center mx-auto my-8"
              @click="show == 1"
            >
              <h3>Overig</h3>
            </div>
          </div>

          <div
            class="bg-gray-700"
            v-for="gerecht in gerechten.Overig"
            :key="gerecht.id"
          >
            <img
              v-if="gerecht.Afbeelding"
              :src="gerecht.Afbeelding.url"
              :alt="gerecht.caption"
              class="w-full h-48 sm:h-56 object-cover"
            />
            <div
              class="text-2xl font-bold gold uppercase text-center mx-auto my-8"
            >
              {{ gerecht.Titel }}
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="py-20 px-8 container mx-auto" id="decoraties">
      <h2 class="gold text-4xl font-bold text-center mb-6">Decoratielijnen</h2>
      <p class="my-4">
        Bij het opzetten van onze decoratielijnen proberen wij onze eigen stijl
        te behouden. Iedere lijn representeert elegantie en klasse op
        simplistische wijze. Hierdoor komen zelfs de kleinste details tot hun
        recht. Met de verscheidene kleurschakeringen en accessoires binnen ons
        assortiment, is er voor ieder wat wils. Maar op aanvraag kunnen wij ook
        hierin aanvullingen of maatwerk leveren. Onze stijl laten wij met alle
        liefde aansluiten op uw wensen.
      </p>
      <div v-for="decoratie in decoraties" :key="decoratie.id">
        <div class="text-2xl font-bold gold uppercase text-center mx-auto my-8">
          {{ decoratie.Titel }}
        </div>

        <Carousel :slides="decoratie.Gallerij" />
      </div>
    </div>
  </section>
</template>

<script>
import _ from 'lodash'
import Carousel from '~/components/Carousel'

export default {
  data() {
    return {
      show: 0,
      decoraties: [],
      gerechten: []
    }
  },
  components: {
    Carousel
  },
  // TODO QUERY
  async mounted() {
    const URL_gerechten = 'https://al-munasabaa.herokuapp.com/gerechtens'
    const URL_decoraties = 'https://al-munasabaa.herokuapp.com/decoraties'
    try {
      const gerechten = await this.$axios.$get(`${URL_gerechten}`)
      this.gerechten = _.groupBy(gerechten, 'Gang')

      this.decoraties = await this.$axios.$get(`${URL_decoraties}`)
    } catch (error) {
      console.error(error)
    }
  }
}
</script>

<style></style>
