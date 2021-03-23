<template>
  <v-form>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-select :value="datasource.project" label="Project" :items="projects"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="datasource.label" label="Label"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-text-field :value="datasource.deviceId" label="Device ID"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-select :value="datasource.manufacturer" label="Manufacturer" :items="manufacturers"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-textarea :value="datasource.description" label="Description"/>
      </v-col>
    </v-row>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-combobox
          :value="datasource.contacts"
          label="Contacts"
          clearable
          multiple
          small-chips
        ></v-combobox>
      </v-col>
    </v-row>
  </v-form>
</template>

<script>
export default {
  data() {
    return {
      projects: [
        'CHS Soilnet',
        'TERENO TOR',
        'TERENO Cosmic Ray Neutron Sensing CRNS',
      ],
      manufacturers: [
        'Campbell',
        'Ecotech',
        'OTT',
      ],

      datasource: {
        project: 'CHS Soilnet',
        deviceId: null,
        manufacturer: null,
        label: null,
        description: null,
        contacts: [],
      },
    }
  },
}
</script>
