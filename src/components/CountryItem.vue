<template>
    <tr>
        <td>{{country.id}}</td>
        <td>{{country.country}}</td>
        <td>{{country.capital}}</td>
        <td><router-link :to="{name: 'edit-country', params: {id: country.id} }" class="btn btn-info">Update</router-link></td>
        <td><button @click="$emit('delete-country', country.id)" class="btn btn-danger">Delete</button></td>
    </tr>
</template>
<script>
export default {
    name: "CountryItem",
    props: ["country"]
}
</script>