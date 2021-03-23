<template>
  <v-container>
    <description :description="description" />
    <shuttle-list :shuttles="shuttles"/>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      description: [
        'Der Abschnitt "Shuttle" beschreibt die Eigenschaften einer Verbindung zwischen der physikalischen\n' +
        'Datenquelle, also im allgemeinen dem Datenlogger, und den die Rohdaten erfassenden und (langfristig) speichernden\n' +
        'Systemen.\n' +
        'Häufig kommt heute dazu FTP als Protokoll zum Einsatz. Perspektivisch wäre die Nutzung von moderneren,\n' +
        'sichereren und für die Echtzeitübertragung optimierten Protokollen erstrebenswert. Dazu zählt aktuell MQTT\n' +
        'aber auch SFTP wäre eine Möglichkeit.',
        'Je nach ausgewähltem Typ werden verschiedene Attribute wie zum Beispiel Host- und Username abgefragt.',
        'Bestimmte Eigenschaften können als Konvention festgelegt werden: z.B. dass die Daten in Verzeichnissen\n' +
        'abgelegt werden müssen, die der Datasource-ID entsprechen oder das Dateinamenpattern die Datasource-ID als\n' +
        'Platzhalter enthält.'
      ],
      show: false,
      shuttles: [{
        id: 1,
        label: 'met-crns01@files.ufz.de',
        type: 'SFTP',
        interval: '5m',
        host: 'files.ufz.de',
        port: 22,
        username: 'rdm-data-ingest-test',
        password: 'ThisIsATopSecretPasswordNobodyWillGetCoronaBeerDrinker',
        path: '/uploads',
        filenamePattern: 'data-*.csv',
      }, {
        id: 2,
        label: 'met-crns01@mqtt.ufz.de',
        type: 'MQTT',
        host: 'mqtt.ufz.de',
        username: 'met-crns01',
        password: 'ThisIsATopSecretPasswordNobodyWillGetCoronaBeerDrinker',
        mqtt: {
          protocol: 'mqtt/tcp',
          client: {
            name: 'met-crns01',
            id: '17351e25-7792-441f-9798-8d5d1d890920',
          }
        },
      }, {
        id: 3,
        type: 'MQTT',
        label: 'met-crns03@mqtt.gfz.de',
        host: 'mqtt.gfz.de',
        username: 'met-crns03',
        password: 'ThisIsATopSecretPasswordNobodyWillGetCoronaBeerDrinker',
        mqtt: {
          protocol: 'mqtt/udp',
          client: {
            name: 'met-crns03',
            id: '17351e25-4567-441f-9798-8d5d1d895555',
          },
        },
      }],
    }
  },
}
</script>
