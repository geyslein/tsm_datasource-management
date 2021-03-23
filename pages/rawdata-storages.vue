<template>
<v-container>
  <description :description="description" />
  <storage-list :storages="storages" />
</v-container>
</template>
<script>
export default {
  data() {
    return {
      description: ['Die Rawdata Storages beschreiben Speicherorte an denen die von den Shuttles transportierten ' +
      'Rohdaten abgelegt werden können. Möglicherweise werden nicht alle Shuttles einen solchen Storage benötigen: ' +
      'Insbesondere Daten, die über Realtime Protokolle wie MQTT transportiert werden könnten ggf. auch direkt an ' +
      'einen Parser übergeben werden, der dann direkt in die Datenbank (Datastore) schreibt.'],
      storages: [{
        id: 1,
        label: 'CRNS MinIO Bucket'
      }, {
        id: 2,
        label: 'CRNS Amzn S3 Bucket'
      }, {
        id: 3,
        label: 'Postgres Rawdata Storage'
      }, {
        id: 4,
        label: 'ORACLE Rawdata Storage'
      },],
    };
  }
}
</script>
