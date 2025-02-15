<template>
  <div class="container">
    <div class="task">
      <div class="title">
        <h1>Trucs à faire</h1>
      </div>
      <!-- Input -->
      <div class="form">
        <input type="text" placeholder="Nouveau truc" v-model="newTask" @keyup.enter="addTodo" />
        <button @click="addTodo"><i class="fas fa-plus"></i></button>
      </div>
      <!-- Liste des trucs -->
      <div class="taskItems">
        <ul>
          <li v-for="task in tasks" :key="task.id">
            <button :class="task.completed ? 'completed' : ''" class="task-title" @click="toggleCompleted({task})">{{ task.title }}</button>
            <button class="trash" @click="deleteTask({task})"><i class="far fa-trash-alt"></i></button>
          </li>
        </ul>
      </div>
      <!-- Boutons -->
      <div class="clearBtns">
        <button @click="clearCompleted">Effacer les trucs faits</button>
        <button @click="clearAll">Effacer tous les trucs</button>
      </div>
      <!-- Trucs en cours -->
      <div class="pendingTasks">
        <span>Trucs en cours: {{ tasks.length }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Task",
  props: ['tasks'],
  data() {
    return {
        newTask: '',
    }

  },
  methods: {
    clearAll(){
      this.tasks = [];
    },
    clearCompleted(){
      let newTasks = this.tasks.filter((task) => task.completed == false);
      this.tasks = newTasks;
    },
    deleteTask(data){
      let id = data.task.id;
      let newTasks = this.tasks.filter((task) => task.id !== id);
      this.tasks = newTasks;
    },
    toggleCompleted(data){
      let task =data.task;
      task.completed = !task.completed;
    },
    addTodo(){
      if(this.newTask){
        this.tasks.push({
          title: this.newTask,
          completed: false,
          id: this.tasks.slice(-1)[0].id + 1
        })
        this.newTask = '';
      }
    }
  }
};
</script>
