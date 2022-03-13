<template>
  <v-container>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :items-per-page="5"
      class="elevation-1"
      @click:row="selectRow"
    ></v-data-table>
    <v-snackbar v-model="snackbar" :left="$vuetify.breakpoint.lgAndUp">
      You have selected {{ currentItem }}
      <v-btn color="pink" text @click="snackbar = false">
        Close
      </v-btn>
    </v-snackbar>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      currentItem: "",
      snackbar: false,      
    };
  },
  props: {
    headers: [],
    desserts: []
  },
  methods: {
    selectRow(event) {
      this.snackbar = true;
      this.currentItem = event.name;
    },
  },
};
</script>

<style>
</style>