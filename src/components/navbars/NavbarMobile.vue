<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light navbar-mobile">
    <div class="container-fluid">
      <button 
        @click="toggleLeftSidebar"
        class="nav-item btn navbar-toggler nav-btn-left" type="button"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <span class="navbar-brand mx-auto">Brand</span>

      <button 
        @click="toggleRightSidebar"
        class="nav-item btn navbar-toggler nav-btn-right" type="button"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
    </div>
    </nav>
</template>

<script>
import { useSidebarStore } from '../../stores/sidebars';

export default {
  name: "NavbarMobile",

  props: ["lSidebar", "rSidebar"],

  methods: {
    toggleLeftSidebar() {
      this.sidebarStore.setRightSidebar(false);
      this.rSidebar.hide();

      if (this.sidebarStore.showLeftSidebar) {
        this.sidebarStore.setLeftSidebar(false);
        this.lSidebar.hide();
        this.sidebarStore.setMainContent(true);
      } else {
        this.sidebarStore.setLeftSidebar(true);
        this.lSidebar.show();
        this.sidebarStore.setMainContent(false);
      }
    },

    toggleRightSidebar() {
      this.sidebarStore.setLeftSidebar(false);
      this.lSidebar.hide();

      if (this.sidebarStore.showRightSidebar) {
        this.rSidebar.hide();
        this.sidebarStore.setRightSidebar(false);
        this.sidebarStore.setMainContent(true);
      } else {
        this.sidebarStore.setRightSidebar(true);
        this.rSidebar.show();
        this.sidebarStore.setMainContent(false);
      }
    }
  },

  setup() {
    const sidebarStore = useSidebarStore();
    return { sidebarStore }
  },
}
</script>