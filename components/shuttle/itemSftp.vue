<template>
  <v-container>
    <v-card-text>
      <v-row>
        <v-col cols="12" md="3">
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Type</v-list-item-title>
              <v-list-item-subtitle>{{ shuttle.type }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Host</v-list-item-title>
              <v-list-item-subtitle>{{ shuttle.host }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-col>
        <v-col cols="12" md="3">
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>User</v-list-item-title>
              <v-list-item-subtitle>{{ shuttle.username }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Password</v-list-item-title>
              <v-list-item-subtitle>
                <v-text-field :value="shuttle.password"
                              :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                              :type="show ? 'text' : 'password'"
                              @click:append="show = !show"
                />
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-col>
        <v-col cols="12" md="3">

          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Path</v-list-item-title>
              <v-list-item-subtitle>{{ shuttle.path }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Filename Pattern</v-list-item-title>
              <v-list-item-subtitle>{{ shuttle.filenamePattern }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-col>
        <v-col cols="12" md="3">

          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Poll interval</v-list-item-title>
              <v-list-item-subtitle>{{ shuttle.interval }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </v-col>
      </v-row>
    </v-card-text>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      show: false,
    }
  },
  props: {
    shuttle: {
      type: Object,
      required: true
    }
  },
}
</script>
