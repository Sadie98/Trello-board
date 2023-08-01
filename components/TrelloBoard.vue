<script setup lang="ts">
import { Column } from "~/types";
import { nanoid } from "nanoid";

const columns = ref<Column[]>([
  {
    id: nanoid(),
    title: "To Do",
    tasks: [
      {
        id: nanoid(),
        title: "Leave the company",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "To Do",
    tasks: [
      {
        id: nanoid(),
        title: "Leave the company",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "In progress",
    tasks: [
      {
        id: nanoid(),
        title: "Find new job",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "In QA",
    tasks: [
      {
        id: nanoid(),
        title: "Feed the cat",
        createdAt: new Date(),
      },
    ],
  },
  {
    id: nanoid(),
    title: "Done",
    tasks: [
      {
        id: nanoid(),
        title: "Eat",
        createdAt: new Date(),
      },
    ],
  },
]);
</script>

<template>
  <div class="flex gap-4 overflow-x-auto items-start">
    <div
      v-for="column in columns"
      :key="column.id"
      class="column bg-gray-200 p-5 rounded min-w-[250px]"
    >
      <header>{{ column.title }}</header>
      <TrelloBoardTask
        v-for="task in column.tasks"
        :task="task"
        :key="task.id"
      />
      <footer>
        <button class="text-gray-500">+ Add a card</button>
      </footer>
    </div>
  </div>
</template>

<style scoped></style>
