<template>
    <v-card>
      <v-card-title>{{ storage.label }}</v-card-title>
      <v-card-actions align="right">
        <item-actions/>
      </v-card-actions>
    </v-card>
</template>
<script>
export default {
  data() {
    return {}
  },
  props: {
    storage: {
      type: Object,
      required: true
    }
  },
}
</script>
