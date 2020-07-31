<template>
    <div class="col-6">
        <h3>Add new country</h3>
        <form @submit="addCountry">
            <div class="form-group">
                <input
                    type="text"
                    name="country"
                    v-model="country"
                    placeholder="Country"
                    class="form-control"
                />
            </div>
            <div class="form-group">
                <input
                    type="text"
                    name="capital"
                    v-model="capital"
                    placeholder="Capital"
                    class="form-control"
                />
            </div>
            <div class="form-group">
                <button class="btn-primary btn">Create</button>
            </div>
        </form>
    </div>
</template>
<script>
export default {
    name: 'AddCountry',
    data() {
        return {
            country: '',
            capital: ''
        }
    },
    methods: {
        addCountry(e) {
            e.preventDefault();
            const newCountry = {
                country: this.country,
                capital: this.capital
            }
            this.$emit('add-country', newCountry);
            this.country = '';
            this.capital = '';
        }
    }
}
</script>