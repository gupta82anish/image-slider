<template>
  <div class="layout">
    <Slider />
  </div>
</template>

<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>
<script>
import Slider from '../components/Slider.vue';
export default {
  name: 'Default',
  components: {
    Slider
  }
}
</script>
<style>
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
}

.layout {
  max-width: 100%;
  /* margin: 0 auto; */
  /* padding-left: 20px; */
  /* padding-right: 20px; */
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;
}

.nav__link {
  margin-left: 20px;
}
</style>
