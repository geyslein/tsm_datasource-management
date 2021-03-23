<template>
  <v-container>
    <v-card v-for="(datasource, idx) in datasources"
            :key="idx"
            :datasource="datasource"
            outlined
            class="mt-5">
      <v-card-title>{{ datasource.label }}</v-card-title>
      <v-card-subtitle>{{ datasource.project }}</v-card-subtitle>
      <v-card-text>
        <v-row>
          <v-col md="3" cols="12">
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Serial number</v-list-item-title>
                <v-list-item-subtitle>{{ datasource.serialNumber }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Description</v-list-item-title>
                <v-list-item-subtitle>{{ datasource.description }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-col cols="12" md="3">
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Project</v-list-item-title>
                <v-list-item-subtitle>{{ datasource.project }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Contacts</v-list-item-title>
                <v-list-item-subtitle>
                  <v-chip-group>
                    <v-chip v-for="(contact, idx) in datasource.contacts" close small :key="idx">
                      {{ contact }}
                    </v-chip>
                  </v-chip-group>
                </v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-col cols="12" md="3">
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Datasource UUID</v-list-item-title>
                <v-list-item-subtitle>{{ datasource.datasourceId }}</v-list-item-subtitle>
              </v-list-item-content>
            </v-list-item>
          </v-col>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Shuttle</v-list-item-title>
              <v-list-item-subtitle>
                <v-expansion-panels focusable>
                  <v-expansion-panel>
                    <v-expansion-panel-header>{{ datasource.shuttle.label }}</v-expansion-panel-header>
                    <v-expansion-panel-content>
                      <shuttle-item :shuttle="datasource.shuttle"/>
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-expansion-panels>
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Rawdata Storage</v-list-item-title>
              <v-list-item-subtitle>
                <v-expansion-panels focusable>
                  <v-expansion-panel>
                    <v-expansion-panel-header>{{ datasource.storage.label }}</v-expansion-panel-header>
                    <v-expansion-panel-content>
                      <storage-item :storage="datasource.storage" />
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-expansion-panels>
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Parser</v-list-item-title>
              <v-list-item-subtitle>
                <v-expansion-panels focusable>
                  <v-expansion-panel>
                    <v-expansion-panel-header>{{ datasource.parser.label }}</v-expansion-panel-header>
                    <v-expansion-panel-content>
                      <parser-item :parser="datasource.parser" />
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-expansion-panels>
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Datastore</v-list-item-title>
              <v-list-item-subtitle>
                <v-expansion-panels focusable>
                  <v-expansion-panel>
                    <v-expansion-panel-header>{{ datasource.datastore.label }}</v-expansion-panel-header>
                    <v-expansion-panel-content>
                      <datastore-item :datastore="datasource.datastore" />
                    </v-expansion-panel-content>
                  </v-expansion-panel>
                </v-expansion-panels>
              </v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-expansion-panels focusable>
            <v-expansion-panel>
              <v-expansion-panel-header>Metrics</v-expansion-panel-header>
              <v-expansion-panel-content>
                <v-list-item>
                  <v-list-item-content>
                    <v-list-item-title>Timestamps received</v-list-item-title>
                    <v-list-item-subtitle>
                      {{ datasource.metrics.timestamps.received | number('0,0', {thousandsSeparator: '.'}) }}
                    </v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-content>
                    <v-list-item-title>Timestamps parsed</v-list-item-title>
                    <v-list-item-subtitle>
                      {{ datasource.metrics.timestamps.parsed | number('0,0', {thousandsSeparator: '.'}) }}
                      ({{ datasource.metrics.timestamps.parsed / datasource.metrics.timestamps.received | percent }})
                    </v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-content>
                    <v-list-item-title>Timestamps stored</v-list-item-title>
                    <v-list-item-subtitle>
                      {{ datasource.metrics.timestamps.stored | number('0,0', {thousandsSeparator: '.'}) }}
                      ({{ datasource.metrics.timestamps.stored / datasource.metrics.timestamps.received | percent }})
                    </v-list-item-subtitle>
                  </v-list-item-content>
                </v-list-item>
              </v-expansion-panel-content>
            </v-expansion-panel>
          </v-expansion-panels>
        </v-row>
      </v-card-text>
      <v-card-actions align="right">
        <item-actions/>
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
    datasources: {
      type: Array,
      required: true
    }
  },
}
</script>
