<template>
  <div id="app" class="antialised">
    <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/favorites">Favorites</router-link>
    </nav>
    <router-view />
  </div>
</template>

<script>
import HomeView from './views/HomeView.vue'
import LikedPhotosView from './views/LikedPhotosView.vue'
export default {
  name: 'app',
  components: {
    HomeView,
    LikedPhotosView
  },
}
</script>

<style lang="scss">
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
