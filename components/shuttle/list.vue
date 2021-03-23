<template>
  <v-container>
    <shuttle-item v-for="(shuttle, idx) in shuttles"
                  :key="idx"
                  :shuttle="shuttle"/>
  </v-container>
</template>
<script>
export default {
  data() {
    return {}
  },
  props: {
    shuttles: {
      type: Array,
      required: true
    }
  },
}
</script>
