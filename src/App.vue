<template>
  <pickup-recipe v-bind:idList="craftingBag" />
  <button v-on:click="addHeart">Add heart</button>
  <item-list :items="items" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import * as d3 from 'd3';
import ItemList from './components/ItemList.vue';
import PickupRecipe from './components/PickupRecipe.vue';

export default defineComponent({
  name: 'App',
  components: {
    PickupRecipe,
    ItemList
  },

  data() {
    return {
      craftingBag: [] as number[],
      items: [] as Element[]
    }
  },

  async created () {
    const items = await this.fetchItems()
    this.items = items
  },

  methods: {
    addHeart() {
      this.craftingBag = [...this.craftingBag, 1]
      console.log(`${this.craftingBag}`)
    },

    resetBag() {
      this.craftingBag = [];
    },

    async fetchItems() {
      const data = await d3.xml("/items.xml")
      const itemArray = []
      for (const n of data.documentElement.querySelectorAll("passive,active,familiar,trinket")) {
        itemArray.push(n)
      }
      return itemArray
    }
  },

  computed: {
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
