<script setup lang="ts">
import { Column, Task } from "~/types";
import { nanoid } from "nanoid";
import draggable from "vuedraggable";
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

const alt = useKeyModifier("Alt");
</script>

<template>
  <div>
    <draggable
      v-model="columns"
      group="columns"
      animation="150"
      handle=".drag-handle"
      item-key="id"
      class="flex gap-4 overflow-x-auto items-start"
    >
      <template #item="{ element: column }: { element: Column }">
        <div class="column bg-gray-200 p-5 rounded min-w-[250px]">
          <header class="font-bold mb-4">
            <DragHandler />
            {{ column.title }}
          </header>
          <draggable
            v-model="column.tasks"
            :group="{ name: 'tasks', pull: alt ? 'clone' : true }"
            handle=".drag-handle"
            animation="150"
            item-key="id"
          >
            <template #item="{ element: task }: { element: Task }">
              <div>
                <TrelloBoardTask
                  :task="task"
                  @delete="
                    column.tasks = column.tasks.filter((t) => t.id !== $event)
                  "
                />
              </div>
            </template>
          </draggable>

          <footer>
            <NewTask @add="column.tasks.push($event)" />
          </footer>
        </div>
      </template>
    </draggable>
  </div>
</template>

<style scoped></style>
