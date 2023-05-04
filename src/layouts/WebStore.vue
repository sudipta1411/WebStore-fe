<template>
  <!-- <q-layout class="ws-store" view="hhh lpR fff"> -->
  <q-layout class="ws-store" view="hHh LpR fff">
    <ws-header />
    <ws-menu v-model="leftDrawerOpen" />
    <q-page-container>
      <ws-stars />
      <router-view />
    </q-page-container>
    <ws-footer />
  </q-layout>
</template>

<script>
import { useQuasar } from "quasar";
import WsHeader from "./WsHeader.vue";
import WsFooter from "./WsFooter.vue";
import WsStars from "../components/WsStars.vue";
import WsMenu from "../components/WsMenu.vue";

export default {
  name: "WsStore",
  data() {
    return {
      leftDrawerOpen: true,
    };
  },
  components: { WsHeader, WsFooter, WsStars, WsMenu },
  mounted() {
    const $q = useQuasar();
    console.log($q.dark.isActive);
    console.log($q.dark.mode);
    console.log(this.$route);
    console.log(this.$router);
  },
};
</script>
<style>
.ws-store .q-page-container :target {
  scroll-margin-top: var(--scroll-margin-top);
}
body.body--light .ws-store {
  background: var(--store-background-color-light);
}
body.body--dark .ws-store {
  background: var(--store-background-color-dark);
}
</style>
