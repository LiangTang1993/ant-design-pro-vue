<template>
  <div class="logo">
    <router-link :to="{name:'aion'}">
      <img src="../../assets/logo.png" width="165px" height="64px" alt="logo" class="logo-size">
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'Logo',
  components: {
  },
  props: {
    title: {
      type: String,
      default: 'AionLegend',
      required: false
    },
    showTitle: {
      type: Boolean,
      default: true,
      required: false
    }
  }
}
</script>
<style>
.logo-size{
  width: 165px!important;
  height: 64px!important;
}
</style>
