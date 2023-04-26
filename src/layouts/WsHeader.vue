<template>
  <q-header
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
      <div class="q-ml-sm row no-wrap items-center">
        <q-btn
          type="a"
          flat
          round
          :icon="!$q.dark.isActive ? 'mdi-desk-lamp-on' : 'mdi-desk-lamp-off'"
          @click="$q.dark.toggle()"
        />
      </div>
    </q-toolbar>
  </q-header>
</template>
<script>
import { useQuasar } from "quasar";
export default {
  mounted() {
    const $q = useQuasar();
    console.log($q);
  },
};
</script>
