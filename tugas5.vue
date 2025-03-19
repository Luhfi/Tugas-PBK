<script setup>
import {ref, computed, watch, onMounted} from 'vue';

const items = ref(['Apple', 'Banana', 'Orange']);
const newItem = ref('');
const itemCount = ref(items.value.length);
const inputRef = ref(null);


const totalItems = computed(() => {
    return items.value.length;
});

watch(items, (newItems) => {
    console.log('Items updated: ', newItems);
    itemCount.value = newItems.length;
}, { deep : true });

function addItem() {
  if (newItem.value.trim() !== '') {
    items.value.push(newItem.value.trim());
    newItem.value = ''; 
  }
}


onMounted(() => {
    if(inputRef.value) {
        inputRef.value.focus();
    }
});

</script>

<template>
    <div>
        <h2>Items List</h2>
        <ul>
            <li v-for="(item, index) in items" :key="index">
                {{ item }}
            </li>
        </ul>

        <input 
            v-model="newItem"
            placeholder="Add New Item"
            ref="inputRef"
        />
        <button @click="addItem">Add item</button>

        <p>Total items: {{ totalItems }}</p>

        <p>Item count (from watchers): {{ itemCount }}</p>
    </div>
</template>