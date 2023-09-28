<template>
  <div id="app">
    <h1>My Task List</h1>
    <task-form></task-form>
    <ul>
      <li v-for="item in TaskItems" :key="item.id">
        <task-item :label="item.label" :done="item.done" :id="item.id"></task-item>
      </li>
    </ul>
  </div>
</template>

<script>
  import TaskItem from './components/TaskItem.vue';
  import TaskForm from './components/TaskForm.vue';
  import uniqueId from 'lodash.uniqueid';

  export default {
    name: 'App',
    components: {
      TaskItem, TaskForm
    },
    data() {
      return {
        TaskItems: [
          {
            id: uniqueId('task-'),
            label: 'Learn Vue',
            done: false
          },
          {
            id: uniqueId('task-'),
            label: 'Create a Vue project with the CLI',
            done: true
          },
          {
            id: uniqueId('task-'),
            label: 'Have fun',
            done: false
          },
        ],
      };
    },
  };
</script>

<!-- <script setup>
  import { ref, onMounted, computed, watch } from 'vue'

  const tasks = ref([])
  const name = ref('')
  const input_content = ref('')
  const input_category = ref(null)
  const tasks_asc = computed(() => tasks.value.sort((a, b) => {
    return a.createdAt - b.createdAt
  }))

  watch(name, (newVal) => {
    localStorage.setItem('name', newVal)
  })

  watch(tasks, (newVal) => {
    localStorage.setItem('tasks', JSON.stringify(newVal))
  }, { deep: true })

  const addTask = () => {
    if (input_content.value.trim === '' || input_category.value === null) {
      return
    }

    tasks.value.push({
      content: input_content.value,
      category: input_category.value,
      done: false,
      createdAt: new Date().getTime()
    })

    input_content.value = ''
    input_category.value = null
  }

  const removeTask = task => {
    tasks.value = tasks.value.filter(t => t !== task)
  }

  onMounted(() => {
    name.value = localStorage.getItem('name') || ''
    tasks.value = JSON.parse(localStorage.getItem('tasks')) || []
  })

</script>

<template>
  <main class="app">
    <section class="greeting">
      <h2>
        Greetings, <input type="text" placeholder="Your name here" v-model="name" />
      </h2>
    </section>
    <section class="create-task">
      <h3>Create Task:</h3>

      <form @submit.prevent="addTask">
        <h4>What is your next task?</h4>
        <input type="text" placeholder="Task content" v-model="input_content" />
        <h4>Business or Personal?</h4>
        <div class="options">
          <label>
            <input type="radio" name="category" value="business" v-model="input_category" />
            <span class="bubble business"></span>
            <div>Business</div>
          </label>
          <label>
            <input type="radio" name="category" value="personal" v-model="input_category" />
            <span class="bubble personal"></span>
            <div>Personal</div>
          </label>
        </div>
        <input type="submit" value="Add Task" />
      </form>
    </section>
    <section class="task-list">
      <h3>Task List:</h3>
      <div class="list">
        <div v-for="task in tasks_asc" :class="`task-item ${task.done && 'done'}`">
          <label>
            <input type="checkbox" v-model="todo.done" />
            <span :class="`bubble ${task.category}`"></span>
          </label>
          <div class="task-content">
            <input type="text" v-model="task.content" />
          </div>
          <div class="actions">
            <button class="remove" @click="removeTask(task)">Remove</button>
          </div>
        </div>
      </div>
    </section>
  </main>
</template> -->


