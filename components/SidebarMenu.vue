<template>
  <b-nav-item :to="path" exact-active-class="sidebar__menu--active" class="sidebar__menu" @click="toggleSidebar()">
    <span>{{ name }}</span>
  </b-nav-item>
</template>

<script>
import { mapMutations } from 'vuex'

export default {
  name: 'SidebarMenu',
  props: {
    name: {
      type: String,
      default: 'Home'
    },
    path: {
      type: String,
      default: ''
    }
  }
}
</script>

<style>
.sidebar__menu {
  transition: background 0.1s ease-in;
}

a {
  display: flex;
  height: 40px;
  color: #4C4C4C;
}

.sidebar__menu--active {
    background-color: #F5F5F5
}
</style>
