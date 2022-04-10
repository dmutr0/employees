<script setup>
import { ref } from "vue";
const emit = defineEmits(["add"]);
const name = ref(""),
  salary = ref("");

function onAdd() {
  emit("add", name.value, salary.value);
  name.value = "";
  salary.value = "";
}
</script>

<template>
  <div className="app-add-form">
    <h3>Добавьте нового сотрудника</h3>
    <form className="add-form d-flex">
      <input
        v-model="name"
        type="text"
        className="form-control new-post-label"
        placeholder="Как его зовут?"
      />
      <input
        v-model="salary"
        type="number"
        className="form-control new-post-label"
        placeholder="З/П в $?"
      />

      <button @click.prevent="onAdd" type="submit" className="btn btn-outline-light">
        Добавить
      </button>
    </form>
  </div>
</template>

<style lang="sass">
.app-add-form
    margin-top: 30px
    padding: 25px
    background-color: #3d5a80
    border-radius: 4px
    box-shadow: 15px 15px 30px rgba(0,0,0, .15)
    color: #fff

.add-form
    margin-top: 20px

.add-form input
    width: 350px
    margin-right: 20px
</style>
