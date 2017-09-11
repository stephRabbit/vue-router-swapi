<template>
  <div class="row align-items-start">
    <Item
        v-for="(item, index) in items"
        :passed-item="item"
        :type="type"
        :key="index"
    />
  </div>
</template>
<script>
  import Item from './Item.vue';

  export default {
    data() {
      return {
        type: this.$route.params.type,
        items: []
      };
    },
    watch: {
      '$route': 'fetchItems'
    },
    methods: {
      fetchItems() {
        this.items = [];
        this.type = this.$route.params.type;
        let intial_ids = [3, 10, 16];

        for (let i in intial_ids) {
          let id = intial_ids[i];

          fetch(`https://swapi.co/api/${this.type}/${id}`, {
            method: 'GET'
          })
            .then(response => response.json())
            .then(json => this.items.push(json));
        }
      }
    },
    created() {
      this.fetchItems();
    },
    components: {
      Item
    }
  };
</script>

