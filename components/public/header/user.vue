<template>
  <div class="m-user">
    <template v-if="user">
      <span class="username">{{ user }}</span>
      <nuxt-link to="/exit">退出</nuxt-link>
    </template>
    <template v-else>
      <nuxt-link to="/login">立即登陆</nuxt-link>
      <nuxt-link to="/register">注册</nuxt-link>
    </template>
  </div>
</template>
<script>
export default {
  data() {
    return {
      user: ''
    }
  }
}

</script>
