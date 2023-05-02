<template>
  <div
    class="ws-search z-max self-center"
    :class="classes"
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
        :name="icon.name"
        @click="icon.onClick"
      />
    </div>
  </div>
</template>
<script>
export default {
  name: "WsSearch",
  data() {
    return {
      hasFocus: false,
      terms: "",
      focusTimer: null,
      focusTime: 150,
    };
  },
  computed: {
    icon() {
      if (this.terms.length > 0) {
        return {
          name: "clear",
          onClick: this.resetSearch,
        };
      } else {
        return { name: "search", onClick: () => {} };
      }
    },
    classes() {
      return this.hasFocus ? "ws-search__focused" : null;
    },
  },
  methods: {
    onClick() {
      this.$refs.inputRef.focus();
      this.onFocusin();
    },
    onFocusin() {
      clearTimeout(this.focusTimer);
      this.hasFocus = true;
    },
    onFocusout() {
      let that = this;
      clearTimeout(this.focusTimer);
      this.focusTimer = setTimeout(() => {
        that.hasFocus = false;
      }, this.focusTime);
    },
    onKeydown(evt) {
      console.log(evt);
    },
    resetSearch() {
      this.terms = "";
    },
  },
};
</script>
<style>
.ws-search {
  width: 350px;
  height: 40px;
}
.ws-search__field {
  width: inherit;
  height: inherit;
  cursor: text;
  transition: box-shadow var(--header-quick-transition) background-color
    var(--header-quick-transition);
}
.ws-search input {
  font-size: var(--font-size);
  width: 1px !important;
  border: 0;
  outline: 0;
  background: none;
}
.ws-search__focused {
  transform: scale3d(1, 1, 1);
}
.ws-search__focused .ws-search__icon {
  display: inline-block !important;
}

@media (min-width: 446px) {
  .ws-search {
    position: relative;
  }
}

body.body--light .ws-search input {
  color: #474747;
}
body.body--light .ws-search__field {
  background: rgb(219, 212, 212);
}
body.body--light .ws-search__focused {
  border: 1px solid #dddddd;
}
body.body--light .ws-search__focused .ws-search__field {
  background-color: rgba(0, 0, 0, 0.28);
}
body.body--dark .ws-search input {
  color: #fff;
}
body.body--dark .ws-search__field {
  background-color: rgba(255, 255, 255, 0.12);
}
body.body--dark .ws-search__icon {
  color: var(--brand-color);
}
/*body.body--dark .ws-search__focused {
  border: 1px solid #2c2a2a;
}*/
body.body--dark .ws-search__focused .ws-search__field {
  background-color: rgba(255, 255, 255, 0.28);
}
</style>
