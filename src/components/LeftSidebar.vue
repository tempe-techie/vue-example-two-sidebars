<template>
  <Transition name="slide">
    <div v-if="sidebarStore.showLeftSidebar" class="p-2 left-col">
      <h3>Left</h3>
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, massa at euismod molestie, elit risus congue 
        elit, non hendrerit metus odio id metus.
      </p>
    </div>
  </Transition>
</template>

<script>
import { useSidebarStore } from '../stores/sidebars';

export default {
  setup() {
    const sidebarStore = useSidebarStore();
    return { sidebarStore }
  }
}
</script>
