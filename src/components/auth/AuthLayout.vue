<template>
<div class="auth-layout row align-content--center">
  <div class="flex xs12 pa-3 flex-center">
    <router-link class="py-5 flex-center" to="/">
      <p class="display-1" style="background-color: rgb(248, 25, 83);">YEON-ENT</p>
    </router-link>
  </div>

  <div class="flex xs12 pa-3">
    <div class="d-flex justify--center">
      <va-card class="auth-layout__card">
        <va-tabs
          v-model="tabIndex"
          center
        >
          <va-tab>로그인</va-tab>
          <va-tab>회원가입</va-tab>
        </va-tabs>

        <va-separator/>

        <div class="pa-3">
          <router-view/>
        </div>
      </va-card>
    </div>
  </div>
</div>
</template>

<script>
import VaIconVuestic from 'vuestic-ui/src/components/vuestic-components/va-icon/va-iconset/VaIconVuestic'

const tabs = [
  'login',
  'signup',
]

export default {
  name: 'AuthLayout',
  components: { VaIconVuestic },
  data () {
    return {
      selectedTabIndex: 0,
      tabTitles: ['login', 'createNewAccount'],
    }
  },
  computed: {
    tabIndex: {
      set (tabIndex) {
        this.$router.push({ name: tabs[tabIndex] })
      },
      get () {
        return tabs.indexOf(this.$route.name)
      },
    },
  },
}
</script>

<style lang="scss">
.auth-layout {
  min-height: 100vh;
  background-image: linear-gradient(to right, #0e4ac4, #002c85);

  &__card {
    width: 100%;
    max-width: 600px;
  }

  &__options {
    @include media-breakpoint-down(xs) {
      flex-direction: column;
    }
  }
}
</style>
