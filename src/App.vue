<template>
  <NavbarMobile v-if="isMobile" :lSidebar="lSidebar" :rSidebar="rSidebar" />
  <NavbarDesktop v-if="!isMobile" />

  <!-- Main content with sidebars -->
  <div class="container-fluid">
    <div class="row flex-nowrap">

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
      lSidebar: null,
      rSidebar: null
    }
  },

  components: {
    LeftSidebar,
    MainContent,
    NavbarDesktop,
    NavbarMobile,
    RightSidebar
  },

  mounted() {
    this.lSidebar = new bootstrap.Collapse('#sidebar1', {toggle: false});
    this.rSidebar = new bootstrap.Collapse('#sidebar2', {toggle: false});

    console.log(this.lSidebar);

    if (this.width < this.breakpoint) {
      console.log("mobile");
      this.sidebarStore.setLeftSidebar(false);
      this.lSidebar.hide();
      this.rSidebar.hide();
      this.sidebarStore.setRightSidebar(false);
    } else {
      this.lSidebar.show();
      this.rSidebar.show();
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
        this.lSidebar.show();
        this.rSidebar.show();
        this.sidebarStore.setLeftSidebar(true);
        this.sidebarStore.setMainContent(true);
        this.sidebarStore.setRightSidebar(true);
      } else {
        this.lSidebar.hide();
        this.rSidebar.hide();
        this.sidebarStore.setLeftSidebar(false);
        this.sidebarStore.setMainContent(true);
        this.sidebarStore.setRightSidebar(false);
      }
    },
  }
}
</script>