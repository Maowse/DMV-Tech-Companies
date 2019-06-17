<template>
  <v-app>
    <v-toolbar app>
      <v-toolbar-title class="headline text-uppercase">
        <span>DMV Tech Companies</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
    </v-toolbar>

    <v-content>
      <company-table></company-table>
    </v-content>
  </v-app>
</template>

<script>
import CompanyTable from './components/CompanyTable.vue';
export default {
  name: 'App',
  components: {
    CompanyTable
  },
  data () {
    return {
      //
    }
  }
}
</script>
