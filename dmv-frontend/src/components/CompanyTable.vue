<template>
  <v-container>
    <v-data-table :items="companies" :headers="headers" :pagination.sync="pagination" class="elevation-1">
      <template v-slot:items="props">
        <td>{{ props.item.Company }}</td>
        <td class="text-xs-right">{{ props.item['City, State'] }}</td>
        <td class="text-xs-right">{{ props.item.Website }}</td>
        <td class="text-xs-right">{{ props.item['Tech Stack'] }}</td>
      </template>
    </v-data-table>
  </v-container>
</template>

<script>
import * as Papa from "papaparse";

export default {
  data: () => {
    return {
      companies: [],
      headers: [
        {
          text: "Company",
          align: "left",
          sortable: true,
          value: "Company"
        },
        { text: "Address", value: '"City, State"', align: "left", sortable: true },
        { text: "Website", value: "Website", align: "left", sortable:true },
        { text: "Tech Stack", value: 'Tech Stack', align:"left", sortable:true }
      ],
      pagination: {
          rowsPerPage: -1
        },
    };
  },
  created() {
    var vm = this;
    function onComplete(event) {
      vm.$set(vm, "companies", event.data);
    }
    Papa.parse(
      "https://raw.githubusercontent.com/Maowse/DMV-Tech-Companies/frontend/companyList.csv",
      { complete: onComplete, delimiter: ",", header: true, download: true }
    );
  }
};
</script>

<style>
</style>
