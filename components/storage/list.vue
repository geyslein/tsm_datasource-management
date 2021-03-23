<template>
  <v-container>
    <v-card v-for="storage in storages" outlined
            :key="storage.id"
            class="mt-5">
      <v-card-title>{{ storage.label }}</v-card-title>
      <v-card-actions align="right">
        <item-actions />
      </v-card-actions>
    </v-card>
  </v-container>
</template>
<script>
export default {
  data() {
    return {}
  },
  props: {
    storages: {
      type: Array,
      required: true
    }
  },
}
</script>
