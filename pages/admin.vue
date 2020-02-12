<template>
  <b-col cols="12" offset="0" md="9" offset-md="3" xl="8" offset-xl="2">
    <b-row>
      <b-col>
        <base-title>Data User</base-title>
      </b-col>
    </b-row>
    <div>
      <b-table responsive striped hover show-empty :items="items" :fields="fields" :busy="isLoading">
        <template slot="empty">
          <p class="text-center mb-0">{{ noResultMessage }}</p>
        </template>
        <template v-slot:table-busy>
          <div class="text-center text-danger my-2">
          </div>
        </template>
        <template v-slot:empty>
          <p class="text-center mb-0">No records to show</p>
        </template>
      </b-table>
    </div>
  </b-col>
</template>

<script>
import BaseTitle from '~/components/BaseTitle'
import BaseInput from '~/components/BaseInput'

export default {
  middleware: 'auth',
  components: { BaseTitle, BaseInput },
  data: () => {
    return {
      filter: '',
      form: {
        user_id: '',
        user_name: '',
        user_username: '',
        user_nip: '',
        user_jabatan: '',
        foto: '',
        isOnline: ''
      },
      fields: [
        { key: 'user_id', label: 'ID', sortable: true },
        { key: 'user_name', label: 'Name', sortable: true },
        { key: 'user_username', label: 'Username', sortable: true },
        { key: 'user_nip', label: 'NIP', sortable: true },
        { key: 'user_jabatan', label: 'Jabatan', sortable: true },
        { key: 'foto', label: 'Foto', sortable: true }
      ],
      isLoading: false
    }
  },
  async asyncData({ $axios, $auth }) {
    const user = await $axios.get('/apix/chat/getuser')
    return { items: user }
    console.log(items)
  },
  // async asyncData ({ $axios, $auth }) {
  //   const user = await $axios.get('/api/profile/me')
  //   return { user: user.data.data.user }
  // },
  methods: {
    resetForm() {
      Object.keys(this.form).forEach(key => (this.form[key] = ''))
    }
  }
}
</script>
