<template lang="html">
  <section class="item-description">
    <div :id="'desc-list-item-' + id">
      <ol>
        <li class="name">{{name}}</li>
        <li class="description">{{description}}</li>
      </ol>
    </div>
  </section>

</template>


<script lang="ts">
import { defineComponent } from 'vue';
  export default  defineComponent({
    name: 'ItemDescription',
    props: {
      id: Number,
      name: String,
      description: String
    },
    // data () {
    //   return {

    //   }
    // },
    // methods: {

    // },
    // computed: {

    // }
})


</script>

<style scoped>
  .item-description {
    border: 2px solid black;
    border-radius: 5px;
  }
</style>
