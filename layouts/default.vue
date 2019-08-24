<template>
  <div class="layout">
    <div class="layout__header">
      <Header />
    </div>

    <div class="layout__page">
      <nuxt />
    </div>
  </div>
</template>

<script>
export default {
  components: {
    Header: () => import('./components/Header')
  }
}
</script>