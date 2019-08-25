<template>
  <div class="header">
    <div 
      class="header__hamburger"
      @click="isDrawerOpen = true"
    >
      <svg width="30" height="18" viewBox="0 0 30 18" fill="none" xmlns="http://www.w3.org/2000/svg">
        <rect width="20" height="2" fill="#2A2A2A"/>
        <rect y="16" width="20" height="2" fill="#2A2A2A"/>
        <rect y="8" width="10" height="2" fill="#2A2A2A"/>
      </svg>
    </div>

    <div class="header__logo">
      Winx la Notte
    </div>

    <drawer 
      :is-open="isDrawerOpen" 
      @close="handleDrawerClose"
    />
  </div>
</template>

<script>
export default {
  data () {
    return {
      isDrawerOpen: true,
    }
  },

  components: {
    Drawer: () => import('./Drawer')
  },

  methods: {
    handleDrawerClose () {
      this.isDrawerOpen = false
    }
  }
}
</script>

<style lang="scss" scoped>
.header {
  height: 54px;

  position: relative;

  background: #FFEAFB;
  box-shadow: 0px 1px 5px rgba(0, 0, 0, 0.1);

  display: flex;
  align-items: center;

  &__hamburger {
    position: absolute;
    top: 0;
    left: 0;

    padding: 18px;
    padding-bottom: 12px;

    &:hover {
      cursor: pointer;
    }
  }

  &__logo {
    margin: 0 auto;

    font-family: 'Lora', serif;
    font-size: 27px;

    user-select: none;
  }
}
</style>