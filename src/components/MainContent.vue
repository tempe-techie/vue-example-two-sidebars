<template>
<Transition name="slide-fade">
  <div v-if="sidebarStore.showMainContent" class="p-2 center-col bg-light">
    <h3>Center</h3>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed euismod, massa at euismod molestie, elit risus congue elit, non 
      hendrerit metus odio id metus.
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
