<template>
  <div id="app">
    <task v-bind:tasks="tasks"></task>
  </div>
</template>

<script>
import Task from "./components/Task";

export default {
  name: "App",
  components: {
    Task,
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: "Sortir le chien",
          completed: false,
        },
        {
          id: 2,
          title: "Faire la vaisselle",
          completed: false,
        },
        {
          id: 3,
          title: "Aller au cinéma",
          completed: false,
        },
      ],
    };
  },
};
</script>