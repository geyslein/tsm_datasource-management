<template>
  <v-list>
    <v-row>
      <v-col md="3" cols="12">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Parsertype</v-list-item-title>
            <v-list-item-subtitle>{{ parser.type }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Delimiter</v-list-item-title>
            <v-list-item-subtitle>{{ parser.delimiter }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
      <v-col md="3" cols="12">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Exclude Headlines</v-list-item-title>
            <v-list-item-subtitle>{{ parser.excludeHeadLines }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Exclude Footer</v-list-item-title>
            <v-list-item-subtitle>{{ parser.excludeFootLines }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
      <v-col md="3" cols="12">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Timestamp Field</v-list-item-title>
            <v-list-item-subtitle>{{ parser.timestampField }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Timestamp Expression</v-list-item-title>
            <v-list-item-subtitle>{{ parser.timestampExpression }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
    </v-row>
  </v-list>
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
