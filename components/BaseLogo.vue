<template>
  <div class="logo">
    <a :href="href" class="logo__img">
      <b-img src="~/assets/img/logo.jpg" :class="{ 'logo__img--small': isSmall }" fluid />
    </a>
  </div>
</template>

<script>
export default {
  name: 'BaseLogo',
  props: {
    isLink: {
      type: Boolean,
      default: false
    },
    isSmall: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    href() {
      return this.isLink ? '/' : false
    }
  }
}
</script>

<style>

.logo {
  display: flex;
  align-items: center;
  justify-content: center;
  position: center;
  padding: 50px;
}
.img-fluid {
    height: 70px;
    max-width: 100%;
}
img {
  height: 100px;
  max-width: 150px;
}
.logo__img--small {
  height: 100px;
  max-width: 200px;
  padding-bottom: 60px;
}

</style>