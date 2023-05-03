<template>
  <q-dialog
    v-model="open"
    no-esc-dismiss
    no-shake
    no-backdrop-dismiss
    transition-show="fade"
    transition-hide="fade"
  >
    <q-card flat bordered class="glassmorphism">
      <q-card-section class="row items-center q-pb-none">
        <div class="text-h6">Login</div>
        <q-space />
        <q-btn icon="close" outline flat round dense v-close-popup />
      </q-card-section>
      <q-separator inset color="orange" />
      <q-card-section>
        <q-btn
          rounded
          color="red"
          icon="mdi-google"
          label="Google"
          @click="gLogin"
        />
        <q-btn rounded color="blue" icon="mdi-facebook" label="Facebook" />
      </q-card-section>
    </q-card>
  </q-dialog>
</template>
<script>
export default {
  name: "LoginDialog",
  props: {
    modelValue: {
      type: Boolean,
      default: false,
      required: true,
    },
  },
  emits: ["update:modelValue"],
  computed: {
    open: {
      get() {
        return this.modelValue;
      },
      set(newValue) {
        this.$emit("update:modelValue", newValue);
      },
    },
  },
  methods: {
    close() {},
    gLogin() {},
  },
};
</script>
