<template>
  <div class="container">
    <GmapMap
      :center="center"
      :zoom="5"
      map-type-id="terrain"
      rounded
      style="
        width: 100%;
        height: 300px;
        border: 6px solid rgb(121, 128, 235);
        border-radius: 15px;
      "
    >
      <GmapMarker
        :key="index"
        v-for="(m, index) in markers"
        :position="m.position"
        :clickable="true"
        :draggable="true"
        @click="center = m.position"
      />
    </GmapMap>
  </div>
</template>
<script>
export default {
  name: 'Map',
  props: {
    lat: {
      type: String,
    },
    log: {
      type: String,
    },
  },
  data() {
    return {
      center: { lat: parseInt(this.lat), lng: parseInt(this.log) },
      markers: [
        {
          position: { lat: parseInt(this.lat), lng: parseInt(this.log) },
        },
      ],
    }
  },
}
</script>
<style scoped>
.vue-map {
  border-radius: 15px;
}
</style>