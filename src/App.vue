<template>
  <div id="ap">
    <HeaderWeb></HeaderWeb>
    <DuAn></DuAn>
    <FooterWeb></FooterWeb>
  </div>
</template>

<script>
import DuAn from '@/components/DuAn.vue';
import FooterWeb from "@/components/FooterWeb.vue";
import HeaderWeb from "@/components/HeaderWeb.vue";

export default {
  name: 'App',
  components: {
    HeaderWeb,
    DuAn,
    FooterWeb,
  },
  mounted() {
    document.title = 'livansport';
  }
}
</script>

<style>
html, body {
  margin: 0;
  padding: 0;
  background: linear-gradient(to right, #ff7e5f, #feb47b);
}
</style>
