<script setup lang="ts">
import ToDoList from './components/ToDoList.vue'
import WelcomeMessage from './components/WelcomeMessage.vue'

</script>

<template>
  <main>
    <WelcomeMessage msg="Webエンジニアになろう講習会へようこそ" />
    <ToDoList />
  </main>
</template>

<style scoped>
main {
  padding: 2rem;
}
</style>
