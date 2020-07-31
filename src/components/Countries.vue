<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Country</th>
                    <th>Capital</th>
                    <th>#</th>
                    <th>#</th>
                </tr>
            </thead>
            <tbody>
                <template v-for="country in countries">
                    <CountryItem
                        v-bind:key="country.id"
                        v-bind:country="country"
                        v-on:delete-country="$emit('delete-country', country.id)"
                    />
                </template>
            </tbody>
        </table>
    </div>
</template>

<script>
import CountryItem from './CountryItem'
export default {
    name: "Countries",
    props: ["countries"],
    components: {
        CountryItem,
    }
}
</script>