<template>
    <div>
        <h3>Import file</h3>
        <form @submit="importData">
            <input
                type="file"
                name="file"
                ref="file"
                @change="handleFileUpload()"
            />
            <button class="btn btn-success">Submit</button>
        </form>
    </div>
</template>
<script>
export default {
    name: "ImportCountries",
    data() {
        return {
            file: '',
        }
    },
    methods: {
        handleFileUpload(){
            this.file = this.$refs.file.files[0];
        },
        importData(e) {
            e.preventDefault();
            let formData = new FormData();
            formData.append('file', this.file);
            this.$emit('import', formData);
            // axios.post(`${API_BASE_URL}/import`, formData, {headers: {'Content-Type': 'multipart/form-data'}})
            //     .then(res => console.log(res))
            //     .catch(err => console.log(err));
        }
    }
}
</script>