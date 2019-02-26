<template lang="pug">
  v-toolbar(fixed dark).cyan
    v-toolbar-title Tab tracker
    v-btn(flat dark @click="navigateTo({name: 'songs'})" ) Browse
    v-spacer
    v-toolbar-items
      v-btn(flat dark @click="navigateTo({name: 'register'})" v-if="!$store.state.isUserLoggedIn") Sign up
      v-btn(flat dark @click="navigateTo({name: 'login'})" v-if="!$store.state.isUserLoggedIn") Login
      v-btn(flat dark @click="logout" v-if="$store.state.isUserLoggedIn") Log Out
</template>

<script>
export default {
  methods: {
    navigateTo (route) {
      this.$router.push(route)
    },
    logout () {
      this.$store.dispatch('setToken', null)
      this.$store.dispatch('setUser', null)
    }
  }
}
</script>
