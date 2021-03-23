<template>
  <v-container>
    <v-card v-for="(parser, idx) in parsers"
            :key="idx"
            :parser="parser"
            outlined
            class="mt-5">
      <parser-item :parser="parser"/>
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
    parsers: {
      type: Array,
      required: true
    }
  },
}
</script>
