<template>
    <div>
        <h3>Export data</h3>
        <div class="dropdown">
  <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
    Export
  </button>
  <div class="dropdown-menu" aria-labelledby="dropdownMenuButton">
    <a class="dropdown-item" :href="csvLink">CSV</a>
    <a class="dropdown-item" :href="xmlLink">XML</a>
    <a class="dropdown-item" :href="jsonLink">JSON</a>
  </div>
</div>
    </div>
</template>
<script>
// import { API_BASE_URL } from '@/config'
export default {
    name: 'Export',
    data() {
        return {
            csvLink: `http://localhost:8000/countries/export?type=csv`,
            jsonLink: `http://localhost:8000/countries/export?type=json`,
            xmlLink: `http://localhost:8000/countries/export?type=xml`,
        }
    }
}
</script>