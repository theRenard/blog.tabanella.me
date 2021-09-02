<template>
  <div class="admin-auth-page">
    <div class="auth-container">
      <form>
        <RInput type="email">E-Mail Address</RInput>
        <RInput type="password">Password</RInput>
        <RButton type="submit">{{ isLogin ? 'Login' : 'Sign Up' }}</RButton>
        <RButton
          type="button"
          btn-style="inverted"
          style="margin-left: 10px"
          @click="isLogin = !isLogin">Switch to {{ isLogin ? 'Signup' : 'Login' }}</RButton>
      </form>
    </div>
  </div>
</template>

<script>
import { RButton, RInput } from '@therenard/renard-ui';

export default {
  name: 'AdminAuthPage',
  components: {
    RInput,
    RButton
  },
  layout: 'admin',
  data() {
    return {
      isLogin: true
    }
  }
}
</script>

<style scoped>
.admin-auth-page {
  padding: 20px;
}

.auth-container {
  border: 1px solid #ccc;
  border-radius: 5px;
  box-shadow: 0 2px 2px #ccc;
  width: 300px;
  margin: auto;
  padding: 10px;
  box-sizing: border-box;
}
</style>

