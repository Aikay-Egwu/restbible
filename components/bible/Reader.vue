<template>
  <div class="grid grid-cols-1">
    <div class="" v-for="(verse, i) in verses" :key="i">
      <p class="py-1 hover:bg-slate-300" >
        <span>{{ i + 1 }}. </span>
        <span>{{ verse }}</span>
      </p>
    </div>  
  </div>
</template>

<script setup>
  
  const {verses} = defineProps(['verses'])

  console.log(verses)

</script>

<style lang="scss" scoped>

</style>