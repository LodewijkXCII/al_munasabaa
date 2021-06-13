<template>
  <div class="modal-mask">
    <div class="modal-wrapper" @click="$emit('close')">
      <div class="modal-container " @click.stop>
        <div class="modal-header">
          <font-awesome-icon :icon="['fas', 'times']" @click="$emit('close')" />
        </div>

        <div class="modal-body">
          <h1 class="gold lg:text-4xl md:text-4xl text-4xl px-5">
            Vraag geheel vrijblijvend een offerte aan
          </h1>
          <form class="p-6 flex flex-col justify-center" @submit="submit">
            <div class="flex flex-col">
              <label for="name" class="hidden">Naam</label>
              <input
                type="name"
                name="name"
                id="name"
                v-model="name"
                placeholder="Naam"
                class="w-100 mt-2 py-3 px-3 rounded-lg bg-white dark:bg-gray-800 border border-gray-400 dark:border-gray-700 text-gray-800 font-semibold focus:border-gold focus:outline-none"
              />
            </div>

            <div class="flex flex-col mt-2">
              <label for="email" class="hidden">Email</label>
              <input
                type="email"
                name="email"
                id="email"
                placeholder="Email"
                v-model="email"
                class="w-100 mt-2 py-3 px-3 rounded-lg bg-white dark:bg-gray-800 border border-gray-400 dark:border-gray-700 text-gray-800 font-semibold focus:border-gold focus:outline-none"
              />
            </div>

            <div class="flex flex-col mt-2">
              <label for="tel" class="hidden">Telefoonnummer</label>
              <input
                type="text"
                name="tel"
                id="tel"
                placeholder="Telefoon nummer"
                v-model="phone"
                class="w-100 mt-2 py-3 px-3 rounded-lg bg-white dark:bg-gray-800 border border-gray-400 dark:border-gray-700 text-gray-800 font-semibold focus:border-gold focus:outline-none"
              />
            </div>
            <div class="flex flex-col mt-2">
              <label for="type" class="hidden">Soort feest</label>
              <input
                type="text"
                name="type"
                id="type"
                placeholder="Soort feest"
                v-model="type"
                class="w-100 mt-2 py-3 px-3 rounded-lg bg-white dark:bg-gray-800 border border-gray-400 dark:border-gray-700 text-gray-800 font-semibold focus:border-gold focus:outline-none"
              />
            </div>
            <div class="flex flex-col mt-2">
              <label for="guest" class="hidden">Aantal gasten</label>
              <input
                type="number"
                name="guest"
                id="guest"
                placeholder="Aantal gasten"
                v-model.number="guest"
                class="w-100 mt-2 py-3 px-3 rounded-lg bg-white dark:bg-gray-800 border border-gray-400 dark:border-gray-700 text-gray-800 font-semibold focus:border-gold focus:outline-none"
              />
            </div>
            <div class="flex flex-col mt-2">
              <label for="package" class="hidden">Gewenst pakket</label>
              <select
                type="package"
                name="package"
                id="package"
                v-model="pakket"
                class="w-100 mt-2 py-3 px-3 rounded-lg bg-white dark:bg-gray-800 border border-gray-400 dark:border-gray-700 text-gray-800 font-semibold focus:border-gold focus:outline-none"
              >
                <option value="" disabled selected hidden
                  >Gewenst pakket</option
                >
                <option
                  v-for="pakket in paketten"
                  :value="pakket.Title"
                  :key="pakket.id"
                  >{{ pakket.Titel }}</option
                >
              </select>
            </div>
            <div class="flex flex-col mt-2 mb-4">
              <label for="location" class="hidden">Locatie</label>
              <input
                type="text"
                name="location"
                id="location"
                placeholder="Locatie"
                v-model="location"
                class="w-100 mt-2 py-3 px-3 rounded-lg bg-white dark:bg-gray-800 border border-gray-400 dark:border-gray-700 text-gray-800 font-semibold focus:border-gold focus:outline-none"
              />
            </div>

            <button
              type="submit"
              class="md:w-32 bg-gold hover:bg-gold-darker text-white font-bold py-3 px-6 rounded-lg mt-3 hover:bg-gold-darker transition ease-in-out duration-300"
            >
              Submit
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {},
  data() {
    return {
      name: '',
      email: '',
      tel: '',
      type: '',
      guest: null,
      pakket: null,
      location: '',
      paketten: []
    }
  },
  methods: {
    submit() {
      // TODO ADD axios post email call
    }
  },
  async created() {
    const data = await this.$axios.$get(
      'https://al-munasabaa.herokuapp.com/pakettens'
    )
    this.paketten = data
  }
}
</script>

<style lang="scss">
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  width: 60%;
  margin: 0px auto;
  padding: 20px 30px;
  background-color: #1d283a;
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.33);
  transition: all 0.3s ease;
}

@media screen and (max-width: 600px) {
  .modal-container {
    width: 100%;
    background: rgba($color: #1d283a, $alpha: 0.4);
    height: 100vh;
  }
}

.modal-header {
  display: flex;
  justify-content: flex-end;

  h3 {
    margin-top: 0;
    // color: $primary-color;
  }

  svg {
    cursor: pointer;
  }
}

.modal-body {
  margin: 20px 0;
}

.modal-default-button {
  float: right;
}
</style>
