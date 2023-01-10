<template>
  <NavbarMobile v-if="isMobile" />
  <NavbarDesktop v-if="!isMobile" />

  <!-- Main content with sidebars -->
  <div class="d-flex flex-column align-items-center mt-3">
    <div class="d-flex main-container">

      <LeftSidebar />
      <MainContent />
      <RightSidebar />
      
    </div>
  </div>
</template>

<script>
import { useSidebarStore } from './stores/sidebars';
import { useBreakpoints } from './composables/useBreakpoints';
import LeftSidebar from './components/LeftSidebar.vue';
import MainContent from './components/MainContent.vue';
import RightSidebar from './components/RightSidebar.vue';
import NavbarDesktop from './components//navbars/NavbarDesktop.vue';
import NavbarMobile from './components//navbars/NavbarMobile.vue';

export default {
  data() {
    return {
      breakpoint: 1000,
    }
  },

  components: {
    LeftSidebar,
    MainContent,
    NavbarDesktop,
    NavbarMobile,
    RightSidebar
  },

  created() {
    if (this.width < this.breakpoint) {
      this.sidebarStore.setLeftSidebar(false);
      this.sidebarStore.setRightSidebar(false);
    }
  },

  computed: {
    isMobile() {
      if (this.width < this.breakpoint) {
        return true;
      }

      return false;
    }
  },

  setup() {
    const sidebarStore = useSidebarStore();
    const { width, type } = useBreakpoints();

    return { sidebarStore, width }
  },

  watch: {
    width(newVal, oldVal) {
      console.log("Width: ", newVal);

      if (newVal > this.breakpoint) {
        this.sidebarStore.setLeftSidebar(true);
        this.sidebarStore.setMainContent(true);
        this.sidebarStore.setRightSidebar(true);
      } else {
        this.sidebarStore.setLeftSidebar(false);
        this.sidebarStore.setMainContent(true);
        this.sidebarStore.setRightSidebar(false);
      }
    },
  }
}
</script>