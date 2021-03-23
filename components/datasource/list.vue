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
          <v-expansion-panels focusable>
            <v-expansion-panel>
              <v-expansion-panel-header>Shuttle</v-expansion-panel-header>
              <v-expansion-panel-content>
                <shuttle-item :shuttle="datasource.shuttle"/>
              </v-expansion-panel-content>
            </v-expansion-panel>
            <v-expansion-panel>
              <v-expansion-panel-header>Rawdata Storage</v-expansion-panel-header>
              <v-expansion-panel-content>
                <storage-item :storage="datasource.storage"/>
              </v-expansion-panel-content>
            </v-expansion-panel>
            <v-expansion-panel>
              <v-expansion-panel-header>Parser</v-expansion-panel-header>
              <v-expansion-panel-content>
                <parser-item :parser="datasource.parser"/>
              </v-expansion-panel-content>
            </v-expansion-panel>
            <v-expansion-panel>
              <v-expansion-panel-header>Datastore</v-expansion-panel-header>
              <v-expansion-panel-content>
                <datastore-item :datastore="datasource.datastore"/>
              </v-expansion-panel-content>
            </v-expansion-panel>
            <v-expansion-panel>
              <v-expansion-panel-header>Metrics</v-expansion-panel-header>
              <v-expansion-panel-content>
                <v-row>
                  <v-col md="3" cols="12">
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
                          ({{
                            datasource.metrics.timestamps.parsed / datasource.metrics.timestamps.received | percent
                          }})
                        </v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                    <v-list-item>
                      <v-list-item-content>
                        <v-list-item-title>Timestamps stored</v-list-item-title>
                        <v-list-item-subtitle>
                          {{ datasource.metrics.timestamps.stored | number('0,0', {thousandsSeparator: '.'}) }}
                          ({{
                            datasource.metrics.timestamps.stored / datasource.metrics.timestamps.received | percent
                          }})
                        </v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-col>
                  <v-col md="6" cols="12">
                    <v-list-item>
                      <v-list-item-content>
                        <v-list-item-title>Last Values ({{ datasource.metrics.latestValues.date }})</v-list-item-title>
                        <v-list-item-subtitle>
                          <v-simple-table>
                            <template>
                              <thead>
                              <tr>
                                <th>Timestamp</th>
                                <th>Channel ID</th>
                                <th>Value</th>
                              </tr>
                              </thead>
                              <tbody>
                              <tr
                                v-for="item in datasource.metrics.latestValues.values"
                                :key="item.channel"
                              >
                                <td>{{ item.timestamp }}</td>
                                <td><a
                                  :href="'https://datasources.ufz.de/' + datasource.datasourceId + '/' + item.channel">{{
                                    item.channel
                                  }}</a></td>
                                <td>{{ item.value }}</td>
                              </tr>
                              </tbody>
                            </template>
                          </v-simple-table>
                        </v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-col>
                </v-row>
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
