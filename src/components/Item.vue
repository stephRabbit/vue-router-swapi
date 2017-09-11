<template>
  <div
    class="col"
    @click="switchItem"
  >
    <div class="character-card">
      <div class="card-block">
        <h4 class="card-title">{{item.name}}</h4>
        <div
          v-for="(value, key, index) in item"
          :key="index"
        >
          <div v-if="index < 5">
            <strong>{{key}}: </strong>{{value}}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['passedItem', 'type'],
    data() {
      return {
        item: {}
      }
    },
    methods: {
      fetchItem(id) {
        fetch(`https://swapi.co/api/${this.type}/${id}`, {
          method: 'GET'
        })
          .then(resopnse => resopnse.json())
          .then(json => this.item = json);
      },
      switchItem() {
        let randomId = Math.floor(Math.random() * 63) + 1;
        this.fetchItem(randomId);
      }
    },
    created() {
      this.item = this.passedItem;
    }
  };
</script>
