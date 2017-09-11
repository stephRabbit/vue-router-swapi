<template>
  <div id="app">
    <h3>{{title}}</h3>
    <h4>
      <router-link class="link" to="/data/people">Characters</router-link> |
      <router-link class="link" to="/data/planets">Planets</router-link>
    </h4>
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      title: 'Star Wars Cards'
    };
  },
  components: {

  }
};
</script>

