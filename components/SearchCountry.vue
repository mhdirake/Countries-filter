<template>
  <div class="container" align="center">
    <v-card width="480">
    <v-form @submit.prevent="filter()">
      <v-container class="d-flex" align="center">
        <v-autocomplete
          :items="countries"
          solo-inverted
          color="blue-grey lighten-2"
          label="search country"
          item-text="name"
          item-value="iso2Code"
          name="name"
          v-model="search"
        >
          <template v-slot:item="country">
            <template>
              <v-list-item-content>
                <v-list-item-title>
                  {{ country.item.name }}
                </v-list-item-title>
              </v-list-item-content>
            </template>
          </template>
        </v-autocomplete>
        <v-btn type="submit" class="ml-2" large color="primary"><v-icon>
          mdi-magnify 
          </v-icon></v-btn>
      </v-container>
    </v-form>
  </v-card>
  </div>
</template>
<script>
export default {
  name: 'SearchCountry',
  data() {
    return {
      search: '',
    }
  },
  props: {
    countries: {
      type: Array,
    },
  },

  methods: {
    filter() {
      this.$router.push('countries/' + this.search)
    },
  },
}
</script>