<template lang="pug">
  v-toolbar(fixed dark).cyan
    v-toolbar-title Tab tracker
    v-spacer
    v-toolbar-items
      v-btn(flat dark @click="navigateTo({name: 'register'})" v-if="!$store.state.isUserLoggedIn") Sign up
      v-btn(flat dark @click="navigateTo({name: 'login'})" v-if="!$store.state.isUserLoggedIn") Login
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    }
  }
}
</script>
