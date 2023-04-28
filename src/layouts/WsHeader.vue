<template>
  <q-header
    :class="$q.dark.isActive ? 'q-header--dark' : 'q-header--light'"
    height-hint="200"
  >
    <q-toolbar class="bruno-font">
      <q-toolbar-title>
        <q-avatar>
          <img src="../assets/painting.svg" />
        </q-avatar>
        WebStore
      </q-toolbar-title>
      <div class="q-ml-sm row no-wrap items-center">
        <q-btn
          v-if="!isLoggedIn"
          type="a"
          flat
          label="Signup"
          @click="signup"
        />
        <q-btn v-if="!isLoggedIn" type="a" flat label="Login" @click="login" />
        <q-btn
          type="a"
          flat
          round
          icon="mdi-instagram"
          href="https://www.instgram.com"
          target="_blank"
        />
        <q-btn
          type="a"
          flat
          round
          icon="mdi-twitter"
          href="https://www.twitter.com"
          target="_blank"
        />
        <q-btn
          type="a"
          flat
          round
          icon="mdi-facebook"
          href="https://www.facebook.com"
          target="_blank"
        />
        <ws-search />
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
  <q-dialog
    v-model="loginDialogOpened"
    no-esc-dismiss
    no-backdrop-dismiss
    transition-show="fade"
    transition-hide="fade"
  >
    <q-card>
      <q-card-section class="row items-center q-pb-none">
        <div class="text-h6">Login</div>
        <q-space />
        <q-btn icon="close" flat round dense v-close-popup />
      </q-card-section>
      <q-card-section>
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum
        repellendus sit voluptate voluptas eveniet porro. Rerum blanditiis
        perferendis totam, ea at omnis vel numquam exercitationem aut, natus
        minima, porro labore.
      </q-card-section>
    </q-card>
  </q-dialog>
</template>
<script>
import { useQuasar } from "quasar";
import WsSearch from "./WsSearch.vue";
export default {
  name: "WsHeader",
  components: { WsSearch },
  data() {
    return {
      isLoggedIn: false,
      loginDialogOpened: false,
    };
  },
  methods: {
    signup() {
      console.log("signup");
    },
    login() {
      console.log("login");
      this.loginDialogOpened = true;
    },
  },
  mounted() {
    const $q = useQuasar();
    console.log($q);
    console.log(this.isLoggedIn);
  },
};
</script>
