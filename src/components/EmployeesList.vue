<script setup>
import EmployeesListItem from "./EmployeesListItem.vue";
defineProps({
  data: Array,
});
</script>

<template>
  <ul className="app-list list-group">
    <li
      v-for="item in data"
      :class="{
        'list-group-item d-flex justify-content-between': true,
        like: item.like,
        increase: item.increase,
      }"
    >
      <EmployeesListItem
        @delete="$emit('delete', item.id)"
        @like="$emit('like', item.id)"
        @increase="$emit('increase', item.id)"
        :key="item.id"
        :name="item.name"
        :salary="item.salary"
      />
    </li>
  </ul>
</template>

<style lang="sass">
.app-list
    margin-top: 30px
    background-color: #3d5a80
    border-radius: 4px
    box-shadow: 15px 15px 30px rgba(0,0,0, .15)
    color: #fff
</style>
