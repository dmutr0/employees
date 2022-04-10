<script setup>
defineProps({
  total: Number,
  onrise: Number,
});
</script>

<template>
  <div class="app-info">
    <h1>Учёт сотрудников компании N</h1>
    <h2>Общее число сотрудников: {{ total }}</h2>
    <h2>Премию получат: {{ onrise }}</h2>
  </div>
</template>

<style>
@import "../assets/base.css";

.app-info {
  background-color: var(--background-color);
  box-shadow: var(--box-shadow);
  border-radius: 4px;
  padding: 25px;
  color: var(--color);
}
</style>
