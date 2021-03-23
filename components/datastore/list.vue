<template>
  <v-container>
    <v-card v-for="datastore in datastores"
            :key="datastore.id"
            outlined
            class="mt-5">
      <datastore-item :datastore="datastore" />
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
    datastores: {
      type: Array,
      required: true
    }
  },
}
</script>
