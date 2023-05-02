<template>
  <q-header
    class="ws-header"
    :class="$q.dark.isActive ? 'q-header--dark' : 'q-header--light'"
    height-hint="200"
  >
    <q-toolbar
      class="bruno-font ws-header-toolbar__primary q-pl-lg no-wrap q-pr-md items-stretch"
    >
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
    <q-card flat bordered class="glassmorphism">
      <q-card-section class="row items-center q-pb-none">
        <div class="text-h6">Login</div>
        <q-space />
        <q-btn icon="close" flat round dense v-close-popup />
      </q-card-section>
      <q-separator inset color="orange" />
      <q-card-section>
        <q-btn
          rounded
          color="red"
          flat
          icon="mdi-google"
          label="Signin with Google"
          @click="gLogin"
        />
        <q-btn
          rounded
          color="blue"
          flat
          icon="mdi-facebook"
          label="Signin with Facebook"
        />
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
    gLogin() {},
  },
  mounted() {
    const $q = useQuasar();
    console.log($q);
    console.log(this.isLoggedIn);
  },
};
</script>
<style>
.ws-header {
  transition: none;
}
.ws-header-toolbar__primary {
  height: var(--toolbar-height);
  border-bottom: 1px solid rgba(0, 0, 0, 0.12);
}
@media (max-width: 320px) {
  .ws-header .q-btn {
    font-size: 12px;
  }
  .ws-header .q-btn--rectangle {
    padding: 8px 2px 8px 10px !important;
  }
}
@media (max-width: 699px) {
  .ws-header .q-toolbar {
    padding-left: 16px;
    padding-right: 8px;
  }
  .ws-header .ws-search {
    width: 100%;
  }
}
@media (min-width: 700px) {
  .ws-header .ws-search {
    margin-left: 8px;
  }
}

body.body--dark .ws-header-toolbar__primary {
  border-bottom-color: rgba(255, 255, 255, 0.28);
}
</style>
