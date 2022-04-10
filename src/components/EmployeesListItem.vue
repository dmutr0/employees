<script setup>
defineProps({
  name: String,
  salary: Number,
});
defineEmits(["increase", "like", "delete"]);
</script>

<template>
  <span @click="$emit('like')" className="list-group-item-label">{{ name }}</span>
  <input type="text" className="list-group-item-input" :defaultValue="salary + '$'" />
  <div className="d-flex justify-content-center align-items-center">
    <button @click="$emit('increase')" type="button" className="btn-cookie btn-sm ">
      <i className="fas fa-cookie"></i>
    </button>

    <button @click="$emit('delete')" type="button" className="btn-trash btn-sm ">
      <i className="fas fa-trash"></i>
    </button>
    <i className="fas fa-star"></i>
  </div>
</template>

<style lang="sass">
.list-group-item
  padding: 15px 20px
  border-bottom: 1px solid #3d5a80

.list-group-item:last-child
  border-bottom: none

.list-group-item span
  line-height: 35px
  font-size: 20px
  cursor: pointer
  min-width: 550px

.list-group-item input
  line-height: 35px
  font-size: 20px
  text-align: center
  border: 0

.list-group-item button
  width: 35px
  height: 35px
  margin: 3px
  font-size: 17px
  border: none
  cursor: pointer

.list-group-item .btn-cookie
  color: #e09f3e


.list-group-item .btn-trash
  color: #e5383b


.list-group-item .fa-star
  width: 35px
  height: 35px
  text-align: center
  line-height: 35px
  font-size: 16px
  color: #ffd700
  transition: 0.3s all
  transform: translateX(30px)
  opacity: 0

.list-group-item.like .fa-star
  opacity: 1
  transform: translateX(0px)

.list-group-item.increase .list-group-item-label,
.list-group-item.increase .list-group-item-input
  color: #e09f3e

.list-group-item.increase .btn-star
  color: #aeaeae
</style>
