<template>
  <q-layout
    class="ws-store"
    view="hhh lpR fff"
    :class="$q.dark.isActive ? 'bg-black' : 'bg-secondary'"
  >
    <ws-header />
    <q-drawer v-model="leftDrawerOpen" side="left" overlay bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
    <ws-footer />
  </q-layout>
</template>

<script>
import { useQuasar } from "quasar";
import WsHeader from "./WsHeader.vue";
import WsFooter from "./WsFooter.vue";

export default {
  name: "WsStore",
  data() {
    return {
      leftDrawerOpen: true,
    };
  },
  components: { WsHeader, WsFooter },
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
</style>
