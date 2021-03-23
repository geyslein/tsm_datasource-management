<template>
  <v-container>
    <v-card-title>{{ parser.label }}</v-card-title>
    <v-card-text>
      <parser-item-csv :parser="parser" v-if="parser.type === 'CSV'"/>
      <parser-item-ecotech :parser="parser" v-if="parser.type === 'ECOTECH'"/>
    </v-card-text>
  </v-container>
</template>
<script>
export default {
  data() {
    return {}
  },
  props: {
    parser: {
      type: Object,
      required: true
    }
  },
}
</script>
