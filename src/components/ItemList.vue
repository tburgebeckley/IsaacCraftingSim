<template lang="html">

  <section class="item-list">
    <div v-for="item in itemsList" :key="item.id">
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
  data () {
    return {}
  },
  methods: {
    convertItemToJson (item: Element) {
      let jsonItem = {
        id: 1,
        name: "defaultName",
        description: "defaultDescription"
      }
      if (item.hasAttributes()) {
        const attributeNames = item.getAttributeNames()
        if ('id' in attributeNames) {
          jsonItem.id = Number(item.getAttribute('id'))
        }
        if ('name' in attributeNames) {
          jsonItem.name = String(item.getAttribute('name'))
        }
        if ('description' in attributeNames) {
          jsonItem.description = String(item.getAttribute('description'))
        }
      }
      return jsonItem
    }

  },
  computed: {
    itemsList: function () {
      return [
        {
          id: 1,
          name: "Cricket's Body",
          description: "Tears up + splash Damage"
        },
        {
          id: 1,
          name: "Cricket's Body",
          description: "Tears up + splash Damage"
        },
        {
          id: 1,
          name: "Cricket's Body",
          description: "Tears up + splash Damage"
        },
        {
          id: 1,
          name: "Cricket's Body",
          description: "Tears up + splash Damage"
        },
        {
          id: 1,
          name: "Cricket's Body",
          description: "Tears up + splash Damage"
        },
      ]
    }
  }
});
</script>

<style scoped>
  .item-list {
    max-width: 100%;
  }
</style>
