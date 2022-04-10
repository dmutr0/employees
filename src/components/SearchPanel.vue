<script setup>
import { ref } from "vue";

const emit = defineEmits(["search"]);

const temp = ref("");

function onSearch(e) {
  temp.value = e.target.value;
  emit("search", temp.value);
}
</script>

<template>
  <input
    type="text"
    className="form-control search-input"
    placeholder="Найти сотрудника"
    :value="temp"
    @input="onSearch"
  />
</template>

<style lang="sass">
.search-panel
    margin-top: 30px
    padding: 25px
    background-color: #3d5a80
    border-radius: 4px
    box-shadow: 15px 15px 30px rgba(0,0,0, .15)
    color: #fff
</style>
