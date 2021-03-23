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
        <v-list-item v-if="parser.failureValue">
          <v-list-item-content>
            <v-list-item-title>Failure Value</v-list-item-title>
            <v-list-item-subtitle>{{ parser.failureValue }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
      <v-col md="3" cols="12">

        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Time Synchronisation</v-list-item-title>
            <v-switch disabled v-model="parser.syncTime" append-icon="mdi-clock"/>
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
