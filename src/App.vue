<template>
  <div id="app">
    <Header></Header>
    <pre
      >{{ $data }}
    </pre>
    <h3>TODOs ({{ todoTasks.length }})</h3>
    <Task
      v-bind:task="task"
      v-for="task in todoTasks"
      :key="task.id"
      @toggle-checked-value="toggleDone"
      @delete-task="deleteTask"
    ></Task>
    <h3>Finished TODOs ({{ completedTasks.length }})</h3>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-bind:class="task.completed ? 'done' : 'todo'"
        v-for="task in completedTasks"
        :key="task.id"
      >
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="checkbox"
              class="form-check-input"
              name="task"
              v-on:click="toggleDone($event, task.id)"
              :checked="task.completed"
            />
            {{ task.description }}
          </label>
        </div>
        <div>
          <font-awesome-icon
            v-on:click="deleteTask($event, task.id)"
            :icon="['fas', 'trash']"
          />
        </div>
      </li>
    </ul>
  </div>
</template>


<script>
import Header from "./components/Header.vue";
import Task from "./components/Task.vue";
export default {
  name: "App",
  data: function () {
    return {
      tasks: [
        { id: 1, description: "task1", completed: false },
        { id: 2, description: "task2", completed: false },
        { id: 3, description: "task3", completed: true },
        { id: 4, description: "task4", completed: true },
      ],
    };
  },
  components: {
    Header,
    Task,
  },
  computed: {
    completedTasks: function () {
      return this.tasks.filter((item) => item.completed == true);
    },
    todoTasks: function () {
      return this.tasks.filter((item) => item.completed == false);
    },
  },
  methods: {
    toggleDone: function (event, id) {
      event.stopImmediatePropagation();
      let task = this.tasks.find((item) => item.id == id);
      if (task) {
        task.completed = !task.completed;
      }
    },
    deleteTask: function (event, id) {
      event.stopImmediatePropagation();
      console.log(event);
      console.log(id);
      let taskIndex = this.tasks.findIndex((item) => item.id == id);
      console.log(taskIndex);
      if (taskIndex > -1) {
        this.$delete(this.tasks, taskIndex);
      }
    },
  },
};
</script>

<style>
</style>
