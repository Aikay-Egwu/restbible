<template>
 <div class="container">
    <div class="text-2xl"></div>
    <NuxtLink to="/">Back</NuxtLink><div class="">Chapters: {{ book.name }}</div>
    <div class="container grid grid-cols-4 gap-3">
      <div class="grid grid-cols-4 gap-2">
        
          <button 
          v-for="(chapter, i) in book.chapters" :key="i"
            class="border-2 py-1 px-1 rounded-md" 
            @click="loadChapter(i)">
            {{ i + 1 }}</button>
        
      </div>
      <div class="col-span-3" v-if="activeChapter">
        <BibleReader :verses="book.verses" />
      </div>
      
    </div>
  </div>
</template>

<script setup>
  import data from '~/data/kjv.json'
  const route = useRoute()
  const book = reactive({verses: [], chapters:[], name: ''})
  const activeChapter = ref()
  //const book = ref({})
  
  //const book = ref(data)
  console.log(book)

  function loadChapter(i) {
    activeChapter.value = i + 1
    console.log(i)
    book.verses = book.chapters[i]
    //console.log("🚀 ~ file: index.vue:31 ~ loadChapter ~ chapter.verses", chapter.verses)
  }

  onMounted(() => {
    const bible = data.find(item => item.name == route.params.book)
    book.chapters = bible.chapters
    book.name = bible.name
    console.log(book)

    //chapter.name = book.name
  })

</script>

<style lang="scss" scoped>

</style>