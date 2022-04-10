<script setup>
import { ref, computed } from "vue";
import AppInfo from "./components/AppInfo.vue";
import SearchPanel from "./components/SearchPanel.vue";
import AppFilter from "./components/AppFilter.vue";
import EmployeesList from "./components/EmployeesList.vue";
import EmployeesAddForm from "./components/EmployeesAddForm.vue";

let id = 1;

const data = ref([
    { name: "John C.", salary: 800, increase: true, like: false, id: id++ },
    { name: "Alex M.", salary: 1300, increase: true, like: true, id: id++ },
    { name: "Carl W.", salary: 950, increase: false, like: false, id: id++ },
  ]),
  temp = ref(""),
  filter = ref("all");

const filteredData = computed(() => {
  const searchedData = data.value.filter((item) =>
    item.name.toLowerCase().startsWith(temp.value.toLocaleLowerCase())
  );
  switch (filter.value) {
    case "all":
      return searchedData;
    case "like":
      return searchedData.filter((item) => item.like);
    case "moreThan1000":
      return searchedData.filter((item) => item.salary >= 1000);
  }
});

function toggleIncrease(id) {
  data.value = data.value.map((item) =>
    item.id === id ? { ...item, increase: !item.increase } : item
  );
}

function toggleLike(id) {
  data.value = data.value.map((item) =>
    item.id === id ? { ...item, like: !item.like } : item
  );
}

function deleteItem(id) {
  data.value = data.value.filter((item) => item.id !== id);
}

function addItem(name, salary) {
  if (name && salary) {
    data.value.push({ name, salary, increase: false, like: false, id: id++ });
  }
}

function searchItem(newTemp) {
  temp.value = newTemp;
}

function changeFilter(newFilter) {
  filter.value = newFilter;
}
</script>

<template>
  <div className="app">
    <AppInfo :total="data.length" :onrise="data.filter((item) => item.increase).length" />

    <div class="search-panel">
      <SearchPanel @search="searchItem" />
      <AppFilter :filter="filter" @filter="changeFilter" />
    </div>

    <EmployeesList
      @delete="deleteItem"
      @like="toggleLike"
      @increase="toggleIncrease"
      :data="filteredData"
    />

    <EmployeesAddForm @add="addItem" />
  </div>
</template>

<style lang="sass">
@import "./assets/base.css"

body
  padding: 50px 0

.app
  max-width: 1000px
  margin: 0 auto
</style>
