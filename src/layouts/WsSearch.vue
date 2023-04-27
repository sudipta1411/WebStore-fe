<template>
  <div
    class="ws-search z-max self-center"
    @click.prevent="onClick"
    @focusin="onFocusin"
    @focusout="onFocusout"
  >
    <div
      class="ws-search__field rounded-borders row items-center no-wrap q-pl-sm q-pr-md"
    >
      <input
        class="col"
        ref="inputRef"
        placeholder="Search..."
        v-model="terms"
        @keydown="onKeydown"
      />
      <q-icon
        class="ws-search__icon cursor-pointer"
        size="24px"
        name="search"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "WsSearch",
  data() {
    return {
      hasFocus: { type: Boolean, value: false },
      terms: { type: String, value: "" },
    };
  },
  methods: {
    onClick() {
      this.$refs.inputRef.focus();
      onFocusin();
    },
    onFocusin() {
      this.hasFocus = true;
    },
    onFocusout() {
      this.hasFocus = false;
    },
    onKeydown(evt) {
      console.log(evt);
    },
  },
};
</script>
<style>
.ws-search {
  width: 400px;
  height: 43px;
}
.ws-search__field {
  width: inherit;
  height: inherit;
  cursor: text;
  transition: box-shadow 0.28s ease-in-out;
}
</style>
