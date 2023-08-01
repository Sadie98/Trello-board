<template>
  <div class="p-10 h-[100vh] bg-teal-600 overflow-auto">
    <h1 class="text-4xl text-white flex items-center mb-10">Trello board</h1>
    <TrelloBoard />
  </div>
</template>
<script setup lang="ts">
import TrelloBoard from "~/components/TrelloBoard.vue";
</script>
