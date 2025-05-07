<template>
  <table class="table">
    <thead>
      <tr>
        <th v-for="column in columns" :key="column.key">
          {{ column.label }}
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(row, rowIndex) in data" :key="rowIndex">
        <td v-for="column in columns" :key="column.key">
          <template v-if="column.key === 'tags'">
            <span v-for="(tag, index) in row[column.key]" :key="index" class="tag">
              {{ tag.toUpperCase() }}
            </span>
          </template>
          <template v-else-if="column.key === 'actions'">
            <button class="btn">Delete</button>
          </template>
          <template v-else>
            {{ row[column.key] }}
          </template>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
defineProps({
  columns: Array,
  data: Array
});
</script>

<style scoped>
.table {
  width: 100%;
  border-collapse: collapse;
  
}

.table th,
.table td {
  border: 1px solid #333    ;
  padding: 8px 12px;
  text-align: left;
}


.tag {
  display: inline-block;
  background-color: #e0e0e0;
  color: #333;
  border-radius: 4px;
  padding: 3px 6px;
  margin-right: 4px;
  font-size: 12px;
}

.btn {
  padding: 4px 8px;
  margin-right: 6px;
  border: none;
  border-radius: 3px;
  cursor: pointer;
  font-size: 13px;
}


</style>