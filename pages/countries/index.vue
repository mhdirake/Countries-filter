<template>
  <div>
    <SearchCountry :countries="countries" />

    <!-- <div> {{ countries }} </div> -->
  </div>
</template>

<script>
import SearchCountry from '@/components/SearchCountry'

export default {
  data() {
    return {
      countries: [],
    }
  },
  components: {
    SearchCountry,
  },
  async fetch() {
    const { data } = await this.$axios.get(
      `http://api.worldbank.org/v2/country?format=json&per_page=299`
    )
    this.countries = data[1]
  },
}
</script>
