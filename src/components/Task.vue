<template>
  <li class="list-group-item" v-bind:class="task.completed ? 'done' : 'todo'">
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
</template>

<script>
export default {
  name: "Task",
  props: ["task"],
  // props: {
  //   task: {
  //     type: Object,
  //   },
  // },
};
</script>
