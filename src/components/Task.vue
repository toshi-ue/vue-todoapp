<template>
  <li class="list-group-item" v-bind:class="task.completed ? 'done' : 'todo'">
    {{ task.id }}<br />
    {{ task.description }}<br />
    {{ task.completed }}<br />
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
