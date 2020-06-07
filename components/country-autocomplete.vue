<template>
  <v-select
    v-model="selectedCountry"
    :options="options"
    @search="onSearch"
    @input="setSelectedAndGo"
  />
</template>

<script>
import { debounce } from 'lodash'
import { mapState } from 'vuex'

export default {
  data: () => ({
    selectedCountry: '',
    options: []
  }),
  computed: {
    ...mapState('location', {
      country: 'country'
    })
  },
  methods: {
    setSelectedAndGo (value) {
      this.$store.dispatch('location/assign', {
        country: value
      })

      this.$router.push('/corona-virus')
    },
    onSearch: debounce(async function (searchString, loading) {
      if (!searchString) {
        loading(false)
        this.options = []
        return
      }

      loading(true)

      await this.$axios.$get(`https://restcountries.eu/rest/v2/name/${searchString}`).then((response) => {
        this.options = response.map(({ name }) => name)
      }).catch(() => {
        this.options = []
      }).finally(() => loading(false))
    }, 300)
  }
}
</script>

<style lang="scss">
@import 'vue-select/dist/vue-select.css';
</style>
