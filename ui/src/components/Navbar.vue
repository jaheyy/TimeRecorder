<template>
  <div>
    <b-navbar type="dark" variant="primary">
      <b-navbar-brand to="/">Time Recorder</b-navbar-brand>

      <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

      <b-collapse id="nav-collapse" is-nav>
        <b-navbar-nav class="ml-auto">
          <b-nav-item v-if="user && user.admin" to="/time-report">Raport czasu</b-nav-item>
          <b-nav-item v-if="user && user.admin" to="/users">Konta użytkowników</b-nav-item>
          <b-nav-item v-if="user && user.admin" to="/tasks">Zadania</b-nav-item>
          <b-nav-item v-if="isLogged" to="/change-password">Zmień hasło</b-nav-item>
          <b-nav-item v-if="isLogged" @click="logout">Wyloguj</b-nav-item>
        </b-navbar-nav>
      </b-collapse>
    </b-navbar>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Navbar',
  computed: mapGetters([
    'isLogged', 'user'
  ]),
  methods: {
    logout() {
      this.$store.dispatch('logout');
      this.$router.push({ name: "Login" });
    },
  },
}
</script>

<style scoped>

</style>
