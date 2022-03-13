<template>
  <v-card elevation="2">
    <v-card-text>
      <div>{{ item.label }}</div>
      <p class="text-h5 text--primary">
        {{ item.value }}
      </p>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: {
    item: {}
  },
};
</script>

<style>
</style>