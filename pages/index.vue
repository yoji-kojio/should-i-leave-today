<template>
  <div class="container">
    <h1 class="title">
      Should I leave my home today?
    </h1>

    <h3 class="subtitle">
      Select your country and discover
    </h3>

    <CountryAutocomplete class="country-autocomplete" />
  </div>
</template>

<script>
import CountryAutocomplete from '~/components/country-autocomplete'

export default {
  components: {
    CountryAutocomplete
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/scss/main.scss';

.container {
  margin: 0 16px;
  display: flex;
  justify-content: center;
  flex-direction: column;
}

.title {
  color: $dark-jungle-green;
}

.subtitle {
  color: $tropical-rain-forest;
  padding-bottom: 15px;
}

.country-autocomplete {
  width: 100%;
}

@media (min-width: $screen-desktop) {
  .container {
    margin: 0 auto;
    min-height: 100vh;
    align-items: center;
    text-align: center;
  }

  .title {
    font-size: 100px;
  }

  .subtitle {
    font-size: 42px;
  }

  .country-autocomplete {
    width: 500px;
  }
}
</style>
