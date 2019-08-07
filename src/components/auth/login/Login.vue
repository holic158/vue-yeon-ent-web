<template>
<form @submit.prevent="onsubmit">
  <va-input
    v-model="email"
    type="email"
    :label="userIdKor"
    :error="!!emailErrors.length"
    :error-messages="emailErrors"
  />

  <va-input
    v-model="password"
    type="password"
    :label="userPwdKor"
    :error="!!passwordErrors.length"
    :error-messages="passwordErrors"
  />

  <div class="auth-layout__options d-flex align--center justify--space-between">
  </div>

  <div class="d-flex justify--center mt-3">
    <va-button type="submit" class="my-0">로그인</va-button>
  </div>
</form>
</template>

<script>
export default {
  name: 'login',
  data () {
    return {
      email: '',
      password: '',
      keepLoggedIn: false,
      emailErrors: [],
      passwordErrors: [],
      userIdKor: '사용자 아이디',
      userPwdKor: '사용자 비밀번호',

    }
  },
  computed: {
    formReady () {
      return !this.emailErrors.length && !this.passwordErrors.length
    },
  },
  methods: {
    onsubmit () {
      // 로그인 API 추가
      this.$router.push({ name: 'data' })
    },
  },
}
</script>

<style lang="scss">
</style>
