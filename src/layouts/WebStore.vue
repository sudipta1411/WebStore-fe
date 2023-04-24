<template>
  <q-layout
    view="hhh lpR fff"
    :class="$q.dark.isActive ? 'bg-black' : 'bg-secondary'"
  >
    <q-header
      elevated
      :class="$q.dark.isActive ? 'q-header--dark' : 'q-header--light'"
      height-hint="200"
    >
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
          </q-avatar>
          WebStore
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" side="left" overlay bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { useQuasar } from "quasar";
export default {
  data() {
    return {
      leftDrawerOpen: true,
    };
  },
  mounted() {
    const $q = useQuasar();
    console.log($q.dark.isActive);
    console.log($q.dark.mode);
  },
};
</script>
