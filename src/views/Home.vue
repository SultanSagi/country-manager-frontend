<template>
  <div id="app" class="container">
    <ImportCountries v-on:import="importCountry" />
    <br>
    <AddCountry v-on:add-country="AddCountry" />
    <br>
    <Countries
      v-bind:countries="countries"
      v-on:delete-country="deleteCountry"
    />
    <Export />
  </div>
</template>

<script>
import Countries from '@/components/Countries';
import ImportCountries from '@/components/ImportCountries';
import AddCountry from '@/components/AddCountry';
import Export from '@/components/Export';
import axios from 'axios';
import { API_BASE_URL } from '@/config';
export default {
  name: 'App',
  components: {
    Countries,
    ImportCountries,
    AddCountry,
    Export
  },
  data() {
    return {
      countries: []
    }
  },
  methods: {
    deleteCountry(id) {
      axios.delete(`${API_BASE_URL}/countries/${id}`)
        .then(() => this.countries = this.countries.filter(c => c.id !== id))
        .catch(err => console.log(err));
    },
    AddCountry(country) {
      axios.post(`${API_BASE_URL}/countries`, {country: country.country, capital: country.capital})
        .then(res => this.countries = [...this.countries, res.data.country])
        .catch(err => console.log(err));
    },
    async importCountry(formData) {
      console.log('import country');
      axios.post(`${API_BASE_URL}/import`, formData, {headers: {'Content-Type': 'multipart/form-data'}})
                .catch(err => console.log(err));
      location.reload();
    }
  },
  created() {
    console.log('create');
    axios.get(`${API_BASE_URL}/countries`)
      .then(res => this.countries = res.data.data)
      .catch(err => console.log(err));
  },
  mounted() {
    console.log('mounted');
  },
}
</script>
