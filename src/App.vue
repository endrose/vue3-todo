<template>
  <div>
    <h1>My Todo</h1>
    <h3>{{ computedAll }}</h3>
    <!--  -->
    <ItemList :Items="DataItemList" @changeItem="CompletedItem" />
  </div>
</template>


<script setup lang="ts">
// import type interface item
import type { ItemInterface } from './models/Items/Item.interface';

import ItemList from '../src/components/items/items.component.vue'

// import reactive
import { reactive, computed } from 'vue';


// create data item
const DataItemList: ItemInterface[] = reactive([
  {
    id: 1,
    name: 'Coffe',
    completed: true
  },
  {
    id: 2,
    name: 'Books ',
    completed: false
  },
  {
    id: 2,
    name: 'Books ',
    completed: false
  },
  {
    id: 2,
    name: 'Books ',
    completed: false
  },
  {
    id: 2,
    name: 'Books ',
    completed: false
  }
])


// fn CompletedItem
const CompletedItem = (id) => {
  alert('Id item' + id);
}

// watch data when change
const computedAll = computed(() => {
  let all = DataItemList.length;
  let countCompleted = 0;

  DataItemList.forEach(element => {
    if (element.completed) {
      countCompleted++;
    }
  });
  return countCompleted == all ? '[ All todo is completed ]' : '[ No ]';

});

</script>
