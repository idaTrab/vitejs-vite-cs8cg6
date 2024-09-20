<template>
  <div id="app" @click="handleDocumentClick">
    <!-- Radial Menu -->
    <div
      v-if="showMenu"
      class="radial-menu"
      :style="{ top: `${menuPosition.y}px`, left: `${menuPosition.x}px` }"
    >
      <div class="menu-item up" @click.stop="selectItem('up')">Up</div>
      <div class="menu-item down" @click.stop="selectItem('down')">Down</div>
      <div class="menu-item left" @click.stop="selectItem('left')">Left</div>
      <div class="menu-item right" @click.stop="selectItem('right')">Right</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showMenu: false,
      menuPosition: { x: 0, y: 0 },
    };
  },
  methods: {
    handleDocumentClick(e) {
      // If the radial menu is visible, clicking outside will close it.
      if (!this.showMenu) {
        this.showMenu = true;
        this.menuPosition = { x: e.clientX, y: e.clientY };
      } else {
        this.showMenu = false;
      }
    },
    selectItem(direction) {
      alert(`You selected: ${direction}`);
      this.showMenu = false; // Hide the menu after selection
    },
  },
};
</script>

<style>
body {
  margin: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #f4f4f4;
}

#app {
  width: 100%;
  height: 100%;
}

.radial-menu {
  position: absolute;
  width: 0;
  height: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}

.menu-item {
  position: absolute;
  width: 80px;
  height: 80px;
  background-color: #3498db;
  border-radius: 50%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  font-family: Arial, sans-serif;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.menu-item:hover {
  background-color: rgb (0);
}

.menu-item.up {
  top: -120px;
  left: -40px;
}

.menu-item.down {
  top: 40px;
  left: -40px;
}

.menu-item.left {
  top: -40px;
  left: -120px;
}

.menu-item.right {
  top: -40px;
  left: 40px;
}
</style>
