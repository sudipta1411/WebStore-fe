<template>
  <q-drawer class="ws-menu" v-model="drawerOpen" side="left" overlay bordered>
    <q-scroll-area class="fit">
      <div class="q-pa-sm">
        <div v-for="menu in menuData" :key="menu.name">
          Drawer {{ menu.name }}
        </div>
      </div>
    </q-scroll-area>
  </q-drawer>
</template>
<script>
export default {
  name: "WsMenu",
  data() {
    return {
      menuData: [],
    };
  },
  props: {
    modelValue: {
      type: Boolean,
      default: true,
    },
  },
  emits: ["update:modelValue"],
  computed: {
    drawerOpen: {
      get() {
        return this.modelValue;
      },
      set(newValue) {
        this.$emit("update:modelValue", newValue);
      },
    },
  },
  methods: {
    setMenuData(menu) {
      console.log(menu);
      this.menuData = menu;
    },
  },
  created() {
    fetch("/src/assets/menu.json")
      .then((resp) => {
        if (resp.ok) {
          return resp.json();
        } else {
          //TODO error handling
        }
      })
      .then((menu) => this.setMenuData(menu))
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
<style>
body.body--light .ws-menu {
  background: var(--menu-bg-color-light);
}
body.body--dark .ws-menu {
  background: var(--menu-bg-color-dark);
}
.ws-menu {
  border-right: 2px solid var(--menu-border-color);
}
</style>
