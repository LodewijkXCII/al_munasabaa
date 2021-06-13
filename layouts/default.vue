<template>
  <div>
    <Navbar />
    <nuxt />
    <Footer />
  </div>
</template>

<script>
import Navbar from '~/components/Navbar.vue'
import Footer from '~/components/Footer.vue'
export default {
  head: {
    return: {
      script: [
        { src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }
      ]
    },
    title: 'Al-Munasaba | Luxary Catering',
    meta: [
      {
        hid: 'description',
        name: 'description',
        content: 'Home page description'
      }
    ]
  },
  components: {
    Navbar,
    Footer
  }
}
</script>

<style lang="scss">
@import '~/assets/scss/main.scss';

h1,
h2,
h3,
h4 {
  font-family: 'Abril Fatface', cursive;
  letter-spacing: 2px;
}

h1,
h2 {
  letter-spacing: 4px;
}

.gold {
  color: $gold-color;
  &-darker {
    color: darken($color: $gold-color, $amount: 5);
  }
}

.bg-gold {
  background-color: $gold-color;
  &-darker {
    background-color: darken($color: $gold-color, $amount: 5);
  }
}

.alblue {
  color: $primary-color;
}

.border-gold {
  border-color: $gold-color;
}
</style>
