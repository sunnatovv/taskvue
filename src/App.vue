<template>
  <div>
    <TreeItem v-for="(item, index) in treeData" :key="index" :item="item" />
    <TableComponent :columns="columns" :data="tableData" class="table"/>
  </div>
</template>

<script setup>
import TreeItem from "./components/TreeItem.vue";

const treeData = [
  {
    title: "Model",
    children: [
      {
        title: "Data warhouse",
        children: [
          {
            title: "asdf",
            children: [
              {
                title: "asdfads",
              },
            ],
          },
        ],
      },
    ],
  },
  {
    title: "Statistics",
    children: [
      {
        title: "hh",
        children: [],
      },
    ],
  },
];


import TableComponent from './components/TableComponent.vue';

const columns = [
  { key: 'name', label: 'Name' },
  { key: 'age', label: 'Age' },
  { key: 'address', label: 'Address' },
  { key: 'tags', label: 'Tags' },
  { key: 'actions', label: 'Action' }
];

const tableData = [
  {
    name: 'John Brown',
    age: 12,
    address: 'New York',
    tags: ['nice', 'dev']
  },
  {
    name: 'Jim Green',
    age: 33,
    address: 'London',
    tags: ['dev']
  },
  {
    name: 'Joe Black',
    age: 45,
    address: 'Sydney',
    tags: ['cool']
  }
];
</script>

<style scoped>
.table{
  margin-top: 100px;
}
</style>