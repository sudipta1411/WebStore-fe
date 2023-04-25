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
