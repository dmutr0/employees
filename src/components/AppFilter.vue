<script setup>
import { computed } from "vue";
const emit = defineEmits(["filter"]);
const props = defineProps({
  filter: String,
});
function onChangeFilter(e) {
  emit("filter", e.target.name);
}

const btns = [
  { name: "all", label: "Все сотрудники" },
  { name: "like", label: "На повышение" },
  { name: "moreThan1000", label: "З/П больше 1000$" },
];

const classedBtns = computed(() =>
  btns.map((btn) => ({
    ...btn,
    classes: btn.name === props.filter ? "btn btn-light" : "btn btn-outline-light",
  }))
);
</script>

<template>
  <div className="btn-group">
    <button
      v-for="btn in classedBtns"
      @click="onChangeFilter"
      :name="btn.name"
      :className="btn.classes"
    >
      {{ btn.label }}
    </button>
  </div>
</template>

<style lang="sass">
.btn-group
    margin-top: 20px
</style>
