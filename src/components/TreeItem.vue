<template>
  <div>
    <div @click="toggle">
      {{ item.title }}
      <span v-if="hasChildren">[{{ isOpen ? "-" : "+" }}]</span>
    </div>

    <div v-if="hasChildren && isOpen">
      <TreeItem v-for="(e, index) in item.children" :key="index" :item="e" />
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import TreeItem from "./TreeItem.vue";

const isOpen = ref(false);

const toggle = () => {
  isOpen.value = !isOpen.value;
};

const props = defineProps({
  item: Object,
});

const hasChildren = computed(() => {
  return props.item.children && props.item.children.length > 0;
});
</script>
