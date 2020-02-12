<template>
  <div class="input">
    <fieldset class="input__group">
      <div class="input__box">
        <input
          :id="id"
          :type="type"
          @input="handleInput"
          :placeholder="placeholder"
          :required="required"
        >
      </div>
    </fieldset>
  </div>
</template>

<script>

export default {
  name: 'BaseInput',
  props: {
    type: {
      type: String,
      default: 'text'
    },
    id: {
      type: String,
      required: true
    },
    placeholder: {
      type: String,
      default: ''
    },
    required: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    handleInput (e) {
      this.$emit('input', e.target.value)
    },
    handleButton (e) {
      this.$emit('click', e)
    }
  }
}
</script>

<style>
.input {
  margin: 30px
}
.input__group {
  margin-bottom: 30px
}
.input__box {
   display: flex;
}
input {
  display: block;
  width: 100%;
  padding: 15px;
  border-radius: 5px;
  border: 0;
  background: #F5F5F5;
  box-shadow: inset 2.5px 2.5px 5px #e9e9e9, inset -2.5px -2.5px 5px white;
  transition: box-shadow 0.1s ease-in;
}
[type='number'] {
  text-align: right;
}
</style>
