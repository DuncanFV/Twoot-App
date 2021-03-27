<template> <!-- for html -->
  <div id="app">
    {{ user.username }} - {{ fullName }}
    <strong>Followers: </strong> {{ followers }}
    <button @click="followUser">
      Follow
    </button>
  </div>
</template>

<script> //for javascript/vue 

export default {
  name: 'App',
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: '@DuncanFV',
        firstName: 'Duncan',
        lastName: 'Ferency-Viars',
        email: 'duncanferencyviars@gmail.com',
        isAdmin: true
      }
    }
  },
  watch: { //allows code to be run when data changes
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`)
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`;
    }
  },
  methods: {
    followUser() {
      this.followers++
    }
  },
  mounted() { //runs when initialized, or reloaded
    this.followUser();
  }
}
</script>

<style> /* for css */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: flex;
  flex-direction: column;
  text-align: center;
}
</style>
