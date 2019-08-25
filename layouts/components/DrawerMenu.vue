<template>
  <div class="menu">
    <div
      v-for="category in menu"
      :key="category.category"
      class="category"
    >
      <div v-if="category.category" class="category__header">        
        <div class="text">
          {{ category.category }}
        </div>

        <div class="line"></div>
      </div>

      <div
        v-for="link in category.items"
        :key="link.title"
        class="category__link"
        :class="{'link--active': link.link === $route.path}"
        @click="handleLinkClick(link.link)"
      >
        <div class="icon" :style="{'--icon-url': `url(${getIconSrc(link.icon)})`}">
          <!-- <img :src="getIconSrc(link.icon)" :alt="`${link.title} icon`"> -->
        </div>

        <div class="text">
          {{ link.title }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      menu: require('./sidebar-menu.yml')
    }
  },

  methods: {
    getIconSrc (iconName) {
      return require(`~/assets/icons/${iconName}.svg`)
    },

    handleLinkClick (path) {
      this.$emit('link-clicked')
      this.$router.push(path)
    }
  }
}
</script>

<style lang="scss" scoped>
.category {
  &__header {
    margin-top: 10px;
    padding: 20px 0;

    display: flex;
    justify-content: center;
    align-items: center;

    position: relative;

    .text {
      color: #CCCCCC;
      text-transform: uppercase;
      user-select: none;
      background: #FFF2FD;
      padding: 0 8px;
      z-index: 1;
    }

    .line {
      position: absolute;
      top: 33px;
      left: 0;
      width: 100%;
      height: 1px;
      background: #CCCCCC;
      z-index: 0;
    }
  }

  &__link {
    font-size: 20px;

    padding: 10px 20px;

    display: grid;
    grid-template-columns: 20px 1fr;
    grid-column-gap: 15px;

    transition: background .2s ease-in;

    user-select: none;

    &.link--active {
      .text {
        color: #4755D5;
      }

      .icon {
        background: #4755D5;
      }
    }

    &:hover {
      background: #00000010;
      cursor: pointer;
    }

    .icon {
      height: 100%;
      background: #2A2A2A;
      mask-image: var(--icon-url);
      mask-repeat: no-repeat;
      mask-position: center;
      mask-size: 20px 20px;
    }

    .icon,
    .text {
      display: flex;
      align-items: center;
    }
  }
}
</style>