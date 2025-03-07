<template>
  <div class="flex flex-col h-full overflow-hidden">
    <Header>
      <h1>Error</h1>
    </Header>
    <div class="flex flex-col overflow-y-auto h-full">
      <LoadingPage v-if="loading" />
      <div v-if="!loading && filteredVerses && filteredVerses.length > 0" class="divider-y">
        <div v-for="(item, index) in filteredVerses" :key="index" class="p-2">
          <div class="flex items-center justify-between">
            <span class="font-semibold select-none">{{ getBookAndChapterName(item.book_number, item.chapter, item.verse) }}</span>
            <div class="flex items-center space-x-2">
              <button class="cursor-pointer outline-none" @click.prevent="copyVerse(item)">
                <copyIcon class="size-5" />
              </button>
              <button class="cursor-pointer outline-none" @click.prevent="toggleFavoriteVerse(item)">
                <bookmarkSlashIcon class="size-5" />
              </button>
            </div>
          </div>
          <button class="select-none text-left" @click.prevent="goToText(item)"><span v-html="$changeTags(item.text)"></span></button>
        </div>
      </div>
      <div v-if="!loading && filteredVerses && filteredVerses.length === 0" class="flex items-center justify-center h-full text-color">
        <div class="flex flex-col items-center space-y-4">
          <p class="select-none">Página Não Encontrada.</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  
</script>

<style>

</style>
