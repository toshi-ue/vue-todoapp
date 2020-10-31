<template>
  <div id="app">
    <Header></Header>
    {{ $data }}
    <h3>TODOs ({{ todoTasks.length }})</h3>
    <Task
      v-bind:task="task"
      v-for="(task, index) in todoTasks"
      :key="index"
    ></Task>
    <h3>Finished TODOS ({{ completedTasks.length }})</h3>
    <ul class="list-group">
      <li
        class="list-group-item"
        v-bind:class="task.completed ? 'done' : 'todo'"
        v-for="(task, index) in completedTasks"
        :key="index"
      >
        <div class="form-check">
          <label class="form-check-label">
            <input
              type="checkbox"
              class="form-check-input"
              name="task"
              :checked="task.completed"
            />
            {{ task.description }}
          </label>
        </div>
        <!-- {{ task.id }}<br /> -->
        <!-- {{ task.description }}<br /> -->
        <!-- {{ task.completed }}<br /> -->
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
};
</script>

<style>
</style>
