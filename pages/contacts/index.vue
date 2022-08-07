<template>
  <div class="contacts-container">
    <h1>Contacts</h1>
    <MapBoxComponent />
  </div>
</template>

<script>
import MapBoxComponent from '../../components/mapbox/Mapbox.vue'

export default {
  name: 'index',
  component: {
    MapBoxComponent,
  }
}
</script>
<style scoped lang="scss">
.contacts-container {
  width: 100%;
  height: 100vh;

  h1 {
    padding-top: 40px;
    font-size: 50px;
    text-align: center;
  }
}
</style>
