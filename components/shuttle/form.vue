<template>
  <v-form>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <shuttle-description />
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-select
          :value="shuttle.type"
          label="Shuttle type"
          :items="shuttleTypes"
        />
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="shuttle.host" label="Host"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-slider
          label="Polling interval"
          :value="shuttle.interval"
          :tick-labels="shuttle.intervals"
          :max="shuttle.intervals.length"
          step="1"
          ticks="always"
          tick-size="4"
        ></v-slider>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="shuttle.port" label="Port"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="shuttle.username" label="Username"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="shuttle.password"
                      label="Password"
                      :append-icon="show ? 'mdi-eye' : 'mdi-eye-off'"
                      :type="show ? 'text' : 'password'"
                      @click:append="show = !show"
        />

      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="shuttle.path" label="Path"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="shuttle.filenamePattern" label="Filename pattern"/>
      </v-col>
    </v-row>
  </v-form>
</template>
<script>
export default {
  data() {
    return {
      show: false,
      description: '\n' +
        '          Der Abschnitt "Shuttle" beschreibt die Eigenschaften einer Verbindung zwischen der physikalischen Datenquelle,\n' +
        '          also im allgemeinen dem Datenlogger, und den die Rohdaten erfassenden und (langfristig) speichernden Systemen.\n' +
        '          Häufig kommt heute dazu FTP als Protokoll zum Einsatz. Perspektivisch wäre die Nutzung von moderneren,\n' +
        '          sichereren und für die Echtzeitübertragung optimierten Protokollen erstrebenswert. Dazu zählt aktuell MQTT\n' +
        '          aber\n' +
        '          auch SFTP wäre eine Möglichkeit.',
      tab: null,
      shuttleTypes: ['SFTP', 'MQTT', 'HTTP', 'FTP'],
      shuttle: {
        type: 'MQTT',
        interval: '5 minutes',
        intervals: [
          '5m',
          '10m',
          '30m',
          '60m',
          '2h',
          '4h',
          '6h',
          '12h',
          '24h',
        ],
        host: null,
        port: 22,
        username: null,
        password: null,
        path: null,
        filenamePattern: null,

      },
    }
  },
}
</script>
