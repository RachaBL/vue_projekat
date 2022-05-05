<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Vase obaveze" :showAddTask="showAddTask" />
    <div v-if="showAddTask">
      <AddTask @add-task="addTask"/>
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks"/>
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    addTask(task) {
      this.task = [...this.tasks, task]
    },
    deleteTask(id){
      if(confirm('Da li ste sigurni da zelite izbrisati task?'))
      this.tasks = this.tasks.filter((task) => task.id !== id)
    },
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id == id ? {...task, reminder: !task.reminder} : task)
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Uciti za ispit',
        day: '10. maj u 14:30',
        reminder: true,
      },
      {
        id: 2,
        text: 'Prosetati psa',
        day: '10. maj u 18:00',
        reminder: true,
      },
      {
        id: 3,
        text: 'Kosarkaska utakmica',
        day: '11. maj u 20:00',
        reminder: false,
      }
    ]
  }
}
</script>

<style>
  .container {
    margin-top: 20px;
    padding: 10px 20px;
    border: 3px solid #e0e0e0;
    border-radius: 5px;
  }
</style>
