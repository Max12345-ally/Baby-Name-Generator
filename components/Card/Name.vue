<script setup lang="ts">
    interface NameProps {
        name:string
    }

const props = defineProps<NameProps>()

</script>

<template>
    <div class="card">
        <h4>{{ name }}</h4>
     </div>

    </template>

  <style scoped>
     .card{
  background-color: rgb(27,60,138);
  width: 29%;
  color:rgb(221, 229, 236);
  border-radius: 1rem;
  padding: 0.1rem;
  margin-right: 0.5rem;
  margin-bottom: 0.5rem;
  position: relative;
}

.card p{
  position: absolute;
  top: -30%;
  left: 93%;
  cursor: pointer;
  color: rgba(255,255,255,0.178)
}
</style>

