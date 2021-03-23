<template>
  <v-list>
    <v-row>
      <v-col cols="12" md="4">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Label</v-list-item-title>
            <v-list-item-subtitle>{{ datastore.label }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Datastore type</v-list-item-title>
            <v-list-item-subtitle>{{ datastore.type }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
      <v-col cols="12" md="4">

        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>URL</v-list-item-title>
            <v-list-item-subtitle>{{ datastore.url }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Username</v-list-item-title>
            <v-list-item-subtitle>{{ datastore.username }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-col>
      <v-col cols="12" md="4">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title>Password</v-list-item-title>
            <v-list-item-subtitle>
              <v-text-field :value="datastore.password"
                            :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                            :type="show ? 'text' : 'password'"
                            @click:append="show = !show"
              />
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
        <v-list-item>
          <v-list-item-content v-if="datastore.schema">
            <v-list-item-title>Schema</v-list-item-title>
            <v-list-item-subtitle>{{ datastore.schema }}</v-list-item-subtitle>
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
    datastore: {
      type: Object,
      required: true
    }
  },
}
</script>
