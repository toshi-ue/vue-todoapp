<template>
  <li class="list-group-item" v-bind:class="task.completed ? 'done' : 'todo'">
    <div class="form-check">
      <label class="form-check-label">
        <input
          type="checkbox"
          class="form-check-input"
          name="task"
          v-on:click="emitReverseCheckedValue($event, task.id)"
          :checked="task.completed"
        />
        {{ task.description }}
      </label>
    </div>
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
  methods: {
    emitReverseCheckedValue: function (event, id) {
      console.log(this);
      console.log(event);
      this.$emit("toggle-checked-value", this.event, id);
    },
  },
};
</script>
