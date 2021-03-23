<template>
  <v-card elevation="22" outlined>
    <v-card-title>Beschreibung</v-card-title>
    <v-card-subtitle v-for="(line, idx) in description " :key="idx">
      {{ line }}
    </v-card-subtitle>
  </v-card>
</template>
<script>
export default {
  data() {
    return {}
  },
  props: {
    description: {
      type: Array,
      required: true
    }
  },
}
</script>

