<template>
  <SideNav :nav-open="showNav" />
  <div :class="['main-body', showNav && 'main-body--nav-open']">
    <TheHeader @menu-click="toggleNav" :nav-open="showNav" />
    <router-view />
  </div>
</template>

<script>
import TheHeader from "@/components/TheHeader.vue";
import SideNav from "@/components/SideNav.vue";

export default {
  name: "App",
  components: {
    TheHeader,
    SideNav
  },
  data() {
    return {
      showNav: true
    };
  },
  methods: {
    toggleNav() {
      this.showNav = !this.showNav;
    }
  }
};
</script>

<style lang="scss">
@import "splitpanes/dist/splitpanes.css";
.main-body {
  position: absolute;
  width: 100%;
  top: 0;
  left: 0;
  transition: left 900ms cubic-bezier(0.215, 0.61, 0.355, 1);
  height: 100%;
  &--nav-open {
    left: 250px;
  }
}
.splitpanes__pane {
  background: none !important;
}

.splitpanes__splitter {
  height: 1px !important;
  border-top: 1px solid black !important;
  margin-top: -1px;
}
</style>
