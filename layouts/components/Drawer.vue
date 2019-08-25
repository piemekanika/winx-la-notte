<template>
  <div
    class="drawer-outer" 
    :class="{'is-open': isOpen, 'is-closing': isClosing}" 
    @click="handleDrawerClose"
  >
    <div class="drawer" @click.stop="() => {}">
      <div class="drawer__header">
        Winx la Notte
      </div>

      <div class="drawer__links">
        <drawer-menu />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: [ 'isOpen' ],

  components: {
    DrawerMenu: () => import('./DrawerMenu')
  },

  data () {
    return {
      isClosing: false,
      
      drawerPosition: 0
    }
  },

  methods: {
    handleDrawerClose () {
      this.isClosing = true

      setTimeout(() => {
        this.$emit('close')
      }, 210)
    }
  }
}
</script>

<style lang="scss" scoped>
@keyframes fadein {
  0% {
    transform: translateX(-300px);
  }

  100% {
    transform: translateX(0);
  }
}

@keyframes fadeout {
  0% {
    transform: translateX(0px);
  }

  100% {
    transform: translateX(-300px);
  }
}

.drawer-outer {
  display: none;

  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;

  transition: background .2s;
  background: #00000000;

  &.is-open {
    display: initial;
    background: #00000028;
  }

  &.is-closing {
    .drawer {
      animation: fadeout .2s;
      animation-fill-mode: forwards;
    }
  }

  .drawer {
    position: absolute;

    animation: fadein .2s;

    left: 0;

    width: 280px;
    height: 100vh;

    background: #FFF2FD;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.25);

    transition: left .2s;

    &__header {
      font-size: 28px;
      text-align: center;
      font-family: 'Lora', serif;

      user-select: none;

      padding: 8px;

      &:hover {
        cursor: pointer;
      }
    }
  }
}
</style>
