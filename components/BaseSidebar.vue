<template>
  <b-col tag="aside" cols="12" md="3" xl="2" class="sidebar p-0" :class="{ 'sidebar--open': isSidebarOpen }">
    <div class="sidebar__menu">
      <b-nav vertical>
        <div class="sidebar__menu--top">
          <sidebar-menu v-for="(menu, key) in menus" :key="key" :name="menu.name" :path="menu.path" />
        </div>
      </b-nav>
    </div>
  </b-col>
</template>

<script>
import { mapState } from 'vuex'
import SidebarMenu from '~/components/SidebarMenu'

export default {
  name: 'BaseSidebar',
  components: { SidebarMenu },
  props: {
    menus: {
      type: Object,
      default: () => {
        return {
          home: {
            name: 'Home',
            path: '/'
          }
        }
      }
    }
  }
}
</script>

<style>
.sidebar__menu {
  position: fixed;
  top: 0;
  height: 100vh;
  z-index: 1040;
  background-color: white;
  transition: transform 0.2s ease-in-out;

}
</style>
