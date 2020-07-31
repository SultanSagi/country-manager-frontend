<template>
    <div>
    <div id="nav">
      <router-link to="/">Home</router-link>
    </div>
    <div class="col-6">
        <h3>Edit country</h3>
        <form @submit="updateCountry">
            <div class="form-group">
                <input
                    type="text"
                    name="country"
                    v-model="country.country"
                    placeholder="Country"
                    class="form-control"
                />
            </div>
            <div class="form-group">
                <input
                    type="text"
                    name="capital"
                    v-model="country.capital"
                    placeholder="Capital"
                    class="form-control"
                />
            </div>
            <div class="form-group">
                <button class="btn-primary btn">Update</button>
            </div>
        </form>
    </div>
    </div>
</template>
<script>
import axios from 'axios';
import { API_BASE_URL } from '@/config';
export default {
    name: 'AddCountry',
    data() {
        return {
            country: {
                country: '',
                capital: ''
            }
        }
    },
    created() {
        const id = this.$route.params.id;
        axios.get(`${API_BASE_URL}/countries/${id}`)
            .then(res => this.country = res.data.data)
            .catch(err => console.log(err));
    },
    methods: {
        updateCountry(e) {
            e.preventDefault();
            axios.patch(`${API_BASE_URL}/countries/${this.$route.params.id}`, {country: this.country.country, capital: this.country.capital})
                .then(() => alert('Updated'))
                .catch(err => console.log(err));
            
        }
    }
}
</script>