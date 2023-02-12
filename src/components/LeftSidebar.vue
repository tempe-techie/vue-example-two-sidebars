<template>
  <div class="col-auto px-0">
    <div id="sidebar1" class="collapse collapse-horizontal border-end" :class="{ show: sidebarStore.showLeftSidebar }">
      <div id="sidebar-nav" class="list-group border-0 rounded-0 text-sm-start min-vh-100">
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-bootstrap"></i> <span>Item</span> </a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-film"></i> <span>Item</span></a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-heart"></i> <span>Item</span></a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-bricks"></i> <span>Item</span></a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-clock"></i> <span>Item</span></a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-archive"></i> <span>Item</span></a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-gear"></i> <span>Item</span></a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-calendar"></i> <span>Item</span></a>
        <a href="#" class="list-group-item border-end-0 d-inline-block text-truncate" data-bs-parent="#sidebar"><i class="bi bi-envelope"></i> <span>Item</span></a>
      </div>
    </div>
  </div>
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
