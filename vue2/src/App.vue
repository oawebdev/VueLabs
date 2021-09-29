<template>
  <div id="app">
    <div id="nav">
      <NavBar
          :variant="variant"
          :type="type"
      />
    </div>
    <router-view/>
  </div>
</template>

<script>
import NavBar from '@/components/nav/NavBar.vue'

export default {
  name: 'App',
  data: () => ({
    variant: "primary",
    type: "dark"
  }),
  components: {
    NavBar
  }
}

</script>
<style>
@import '~bootstrap/dist/css/bootstrap.css';
@import '~bootstrap-vue/dist/bootstrap-vue.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
/*
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}*/
</style>
