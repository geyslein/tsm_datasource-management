<template>
  <v-container>
    <description :description="description" />
    <parser-list :parsers="parsers"/>
  </v-container>
</template>
<script>
export default {
  data() {
    return {
      description: ['Im Abschnitt "Parser" werden die Eigenschaften der verschiedenen Parsertypen verwaltet. Ein heute gängiger\n' +
      'Parsertyp wäre z.B. "CSV". Je nach Typ werden verschiedene Attribute wie z.B. Feldtrenner oder Position der\n' +
      'Zeitstempel festgelegt.'],
      parsers: [{
        label: 'GCEF IMMS CSV Parser',
        type: 'CSV',
        delimiter: ',',
        excludeHeadLines: 2,
        excludeFootLines: 0,
        timestampField: 1,
        timestampExpression: 'yyyy-mm-dd hh24:mi:ss',
      }, {
        label: 'Ecotech Binary Parser v1',
        type: 'ECOTECH',
        syncTime: true,
      }, {
        label: 'Ecotech Binary Parser 2021',
        type: 'ECOTECH',
        syncTime: false,
        failureValue: -9999,
      }],
    };
  }
}
</script>
