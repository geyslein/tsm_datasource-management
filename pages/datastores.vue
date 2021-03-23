<template>
  <v-container>
    <description :description="description"/>
    <datastore-list :datastores="datastores"/>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      description: ['Der Abschnitt Datastore beschreibt die konfigurierbaren Eigenschaften der anbindbaren' +
      ' Datenhaltungssysteme. Je nach Typ können ggf. unterschiedliche Attribute erfasst werden.'],
      datastores: [{
        type: 'TIMESCALE',
        label: 'TOR Schema on TimescaleDB',
        url: 'postgresql://timescale.intranet.ufz.de:5432/tor',
        username: 'tor',
        password: 'HideMeIfYouCan4711',
      }, {
        type: 'POSTGRES',
        label: 'TOR Schema on Postgres',
        url: 'postgresql://postgres.intranet.ufz.de:5432/tor',
        username: 'tor',
        password: 'HideMeIfYouCan4711',
      }, {
        type: 'ORACLE',
        label: 'WKDV Datacenter Energy Monitoring',
        url: 'jdbc:oracle:thin:@ldap://tnsnames.intranet.ufz.de:389/LOGGER,cn=OracleContext,dc=ufz,dc=de',
        username: 'wkdv-energy-monitoring',
        password: 'HideMeIfYouCan4711',
        schema: 'COMA',
      }, {
        type: 'INFLUX',
        label: 'WKDV Datacenter Energy Monitoring with Influx',
        url: 'influx://webapps.ufz.de/wkdv-energy-monitoring/influx01',
        username: 'wkdv-energy-monitoring',
        password: 'HideMeIfYouCan4711',
      },],
    };
  }
}
</script>
