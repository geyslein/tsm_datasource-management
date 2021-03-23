<template>
      <v-card outlined elevation="22" class="mt-5">
        <v-card-title>{{ shuttle.label }}</v-card-title>
        <shuttle-item-mqtt v-if="shuttle.type === 'MQTT'" :shuttle="shuttle"/>
        <shuttle-item-sftp v-if="shuttle.type === 'SFTP'" :shuttle="shuttle"/>
        <v-card-actions align="right">
          <item-actions/>
        </v-card-actions>
      </v-card>
</template>
<script>
export default {
  data() {
    return {
      show: false,
    }
  },
  props: {
    shuttle: {
      type: Object,
      required: true
    }
  },
}
</script>
