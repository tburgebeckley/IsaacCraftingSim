<template lang="html">

  <section class="item-list">
    <div v-for="item in items" :key="item.id">
        <item-description v-bind="item" />
    </div>
  </section>

</template>

<script lang="ts">
import { defineComponent } from 'vue';
import ItemDescription from './ItemDescription.vue'

export default defineComponent({
  name: 'item-list',
  components: {
    ItemDescription
  },
  props: {
    items: Array
  },
  methods: {
  },
  computed: {
  }
});
</script>

<style scoped>
  .item-list {
    max-width: 100%;
  }
</style>
