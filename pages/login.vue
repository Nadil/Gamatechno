<template>
  <b-col
    cols="12"
    offset="0"
    md="10"
    offset-md="1"
    xl="8"
    offset-xl="2"
  >
    <b-row tag="section" class="content align-items-center">
      <b-col cols="12" offset="0" md="8" offset-md="2">
        <base-logo is-link />
        <b-form class="form">
          <base-input
            id="username"
            v-model="form.username"
            type="text"
            placeholder="Username"
            class="mt-2"
            required
          />
          <p v-if="username.isInvalid" style="color:red">
            {{ username.message }}
          </p>
          <base-input
            id="password"
            v-model="form.password"
            type="password"
            placeholder="Password"
            class="mt-2"
            required
          />
          <p v-if="password.isInvalid" style="color:red">
            {{ password.message }}
          </p>
          <b-button size="lg" variant="warning" @click.prevent="handleLogin" type="submit">
            Login
          </b-button>
        </b-form>
      </b-col>
    </b-row>
  </b-col>
</template>

<script>
import BaseInput from '~/components/BaseInput'
import BaseLogo from '~/components/BaseLogo'

export default { 
  components: { BaseInput, BaseLogo },
  data: () => {
    return {
      form: {
        username: '',
        password: ''
      },
      username: {
        isInvalid: false,
        message: ''
      },
      password: {
        isInvalid: false,
        message: ''
      }
    }
  },
  methods: {
    handleLogin () {
       this.resetForm()
      if (this.form.username === '' || this.form.password === '') {
        this.password.isInvalid = true
        this.password.message = 'Fill all the field'
      } else {
        this.$auth
          .loginWith('local', {
            data: {
              username: this.form.username,
              password: this.form.password,
              type: 'INTERNAL'
            }
          })
          .then(() => {
            this.$router.push(`/admin`)
          })
        .catch(({ err }) => {
            if (err.response.data.error.errors[0] === 'Invalid Password') {
              this.password.isInvalid = true
              this.password.message = err.response.data.error.errors[0]
            } else {
              this.username.isInvalid = true
              this.username.message = err.response.data.error.errors[0]
            }
          })
      }
    },
    resetForm () {
      this.username.isInvalid = false
      this.password.isInvalid = false
      this.username.message = ''
      this.password.message = ''
    }
  }
}
</script>

<style>
form {
  background-color: #C0C0C0;
  box-shadow: 10px 10px 10px #e9e9e9, -10px -10px 10px #ffffff;
  border-radius: 10px;
  padding: 30px 30px 10px;
  margin-bottom: 50px;
}
.content {
  min-height: calc(100vh - 50px);
  padding-top: 0;
  padding-bottom: 50px;
}
</style>