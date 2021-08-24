<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <LoginComp />
  </div>
</template>

<script>
import LoginComp from '@/components/LoginComp.vue'

export default {
  name: 'Home',
  components: {
    LoginComp
  }
}
</script>
