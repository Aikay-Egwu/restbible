<template>
  <div>
    home
    <div class="">Books: {{ books }}</div>
    <div class="container">
      <div class="grid grid-cols-7">
        <div class="" v-for="(book, i) in bible" :key="i">
          <NuxtLink :to="book.name">{{ book.name }}</NuxtLink>
      
    </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  import data from '~/data/kjv.json'

  const books = ref(0)
  const bible = ref()

  onMounted(() => {
    console.log(data)
    bible.value = data
    books.value = data.length
  })
</script>

<style lang="scss" scoped>

</style>