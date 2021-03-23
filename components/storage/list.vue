<template>
  <v-container>
    <storage-item v-for="storage in storages" outlined
            :key="storage.id"
            class="mt-5"
            :storage="storage" />
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
