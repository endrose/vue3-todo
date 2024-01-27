<template
>
  <h3>Item List</h3>
  <!-- show items -->
  <ul v-for="data in Items" :key="data.id">
    <li>
      {{ data.name }} - <input @click="completedItems(data.id)" type="checkbox" v-model="data.completed">
    </li>
  </ul>
</template>

<script setup lang="ts">
//import type interface item
import type { ItemInterface } from '../../../src/models/Items/Item.interface'
// define prop data
defineProps<{ Items: ItemInterface[] }>();


// Emit FN
const emit = defineEmits<{ (e: 'changeItem', id: number): any }>();



// Function completed items
const completedItems = (id) => {
  // test id item 1 
  emit('changeItem', id);
}

</script>