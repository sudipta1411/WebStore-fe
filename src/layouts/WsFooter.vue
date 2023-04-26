<template>
  <q-footer :class="$q.dark.isActive ? 'q-footer--dark' : 'q-footer--light'">
    <q-toolbar>
      <q-toolbar-title>
        <q-avatar>
          <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg" />
        </q-avatar>
        Title
      </q-toolbar-title>
    </q-toolbar>
  </q-footer>
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
