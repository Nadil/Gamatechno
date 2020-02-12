<template>
  <div>
    <b-container fluid>
      <b-row tag="section" class="content admin">
        <base-sidebar :menus="menus" />
        <nuxt />
      </b-row>
    </b-container>
  </div>
</template>

<script>
import BaseSidebar from '~/components/BaseSidebar'

export default {
  components: { BaseSidebar },
  middleware: 'aadmin',
  data: () => {
    return {
      menus: {
        home: {
          name: 'Data User',
          path: '/admin'
        },
      }
    }
  }
}
</script>