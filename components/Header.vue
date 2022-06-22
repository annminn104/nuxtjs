<template>
  <a-layout-header>
    <div class="logo"></div>
    <a-menu
      v-model:selectedKeys="selectedKeys"
      theme="dark"
      mode="horizontal"
      :style="{ lineHeight: '64px' }"
    >
      <a-menu-item>
        <nuxt-link to="/">Home</nuxt-link>
      </a-menu-item>
      <a-menu-item>
        <nuxt-link to="/mountains">Mountains</nuxt-link>
      </a-menu-item>
    </a-menu>
  </a-layout-header>
</template>
<style>
a.nuxt-link-active {
  font-weight: bold;
}
/* exact link will show the primary color for only the exact matching link */
a.nuxt-link-exact-active {
  color: #00c58e !important;
}
</style>
