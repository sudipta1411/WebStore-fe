<template>
  <q-layout class="ws-store" view="hhh lpR fff">
    <ws-header />
    <q-drawer v-model="leftDrawerOpen" side="left" overlay bordered>
      <!-- drawer content -->
    </q-drawer>

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

export default {
  name: "WsStore",
  data() {
    return {
      leftDrawerOpen: true,
    };
  },
  components: { WsHeader, WsFooter, WsStars },
  mounted() {
    const $q = useQuasar();
    console.log($q.dark.isActive);
    console.log($q.dark.mode);
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
