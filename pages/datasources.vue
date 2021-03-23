<template>
  <v-container>
    <description :description="description"/>
    <datasource-list :datasources="datasources"/>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      description: [
        'Die Datasource ist (überraschung!) **das zentrale Element** des Datasource Management Systems.',
        'An der Datasource werden die verschiedenen Elemente des "Time Series Data Ingress" zusammengeführt.',
        '...TBC!',
      ],
      show: false,
      datasources: [{
        id: 1,
        project: 'Cosmic Ray Neutron Sensing',
        label: 'Cosmic Ray Neutron Sensing Station Cummersbach',
        serialNumber: '456477999888',
        description: 'Static station in the area of Cummersbach',
        contacts: [
          'Martin S.',
          'David',
          'Daniel',
        ],
        datasourceId: '33c4e048-caad-4ab6-b46e-295ea438f343',
        shuttle: {
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
        },
        storage: {
          id: 1,
          label: 'CRNS MinIO Bucket'
        },
        parser: {
          label: 'GCEF IMMS CSV Parser',
          type: 'CSV',
          delimiter: ',',
          excludeHeadLines: 2,
          excludeFootLines: 0,
          timestampField: 1,
          timestampExpression: 'yyyy-mm-dd hh24:mi:ss',
        },
        datastore: {
          type: 'POSTGRES',
          label: 'TOR Schema on Postgres',
          url: 'postgresql://postgres.intranet.ufz.de:5432/tor',
          username: 'tor',
          password: 'HideMeIfYouCan4711',
        },
        metrics: {
          timestamps: {
            received: 2342666,
            parsed: 1342000,
            stored: 1102000,
          }
        }
      }, {
        id: 2,
        project: 'Cosmic Ray Neutron Sensing',
        label: 'Cosmic Ray Neutron Sensing Rover ',
        serialNumber: '456477999888445466',
        description: 'Mobile car rover driving around',
        contacts: ['Martin S.'],
        datasourceId: '33c4e048-caad-4ab6-b46e-295ea438f343',
        shuttle: {
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
        },
        storage: {
          id: 2,
          label: 'CRNS Amzn S3 Bucket'
        },
        parser: {
          label: 'Ecotech Binary Parser 2021',
          type: 'ECOTECH',
          syncTime: false,
          failureValue: -9999,
        },
        datastore: {
          type: 'INFLUX',
          label: 'WKDV Datacenter Energy Monitoring with Influx',
          url: 'influx://webapps.ufz.de/wkdv-energy-monitoring/influx01',
          username: 'wkdv-energy-monitoring',
          password: 'HideMeIfYouCan4711',
        },
        metrics: {
          timestamps: {
            received: 2342666,
            parsed: 1342000,
            stored: 1233000,
          }
        }
      },],
    }
  },
}
</script>
