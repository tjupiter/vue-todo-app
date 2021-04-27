<template>
  <div class="max-w-lg border border-gray-400 my-6 py-3 mx-auto">
     
    <div class="flex justify-between items-center px-4">
        <Header title="Task Tracker" />
        <div >
          <Button 
          @btn-click="toggleAddTask"
          :text="showAddTask ? 'Close' : 'Add Task'"
          
          :tailwindColor="showAddTask ? 'border-red-900 bg-red-500 hover:bg-red-400' : 'border-blue-900 bg-blue-500 hover:bg-blue-400'" />
          <!-- <Button text="Add task" tailwindColor="border-green-900 bg-green-500 hover:bg-green-400" />
          <Button text="Add task" tailwindColor="border-blue-900 bg-blue-500 hover:bg-blue-400" /> -->
        </div>
    </div>
    
    <div v-show="showAddTask" class="space-y-4 mt-4 mx-3">
       <AddTask @add-task="addTask" />
    </div>
    
    <div> 
        <Tasks 
        @toggle-reminder="toggleReminder"
        @delete-task="deleteTask" 
        :tasks="tasks" />
    </div>
     
  </div>
</template>

<script>

import Header from './components/Header'
import Button from './components/Button'
import Tasks from  './components/Tasks'
import AddTask from  './components/AddTask'

export default {
  name: 'App',

  components: {
    Header,
    Button,
    Tasks,
    AddTask,
  },

  data() {
    return {
      tasks: [],
      showAddTask: false,
    }
  },

  methods: {
    addTask(task) {
      this.tasks = [...this.tasks, task]
    },

    toggleAddTask() {
      this.showAddTask = !this.showAddTask;
    },


    deleteTask(id) {
      if (confirm('Are you sure?')) {
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, reminder: !task.reminder} : task)
    } 
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Doctors Appointment',
        day: 'March 1st at 2:30pm',
        reminder: true,
      },
      
      {
        id: 2,
        text: 'Meeting at School',
        day: 'March 3rd at 1:30pm',
        reminder: true,
      },

      {
        id: 3,
        text: 'Food Shopping',
        day: 'March 3rd at 11:00am',
        reminder: false,
      }
    ]
  }
}
</script>

<style>

</style>
