<template>
  <div class="sub-content-element">
    <h3>Todo</h3>
    <p>
      <span>
        <button
          class="btn-danger"
          @click="taskCompleted = !taskCompleted"
        >Hide/Show completed task(s)</button>
      </span>
      <span>
        <button class="btn-danger" @click="$emit('delete:tasks')">Delete All</button>
      </span>
    </p>
    <p v-if="this.tasks.filter(this.inProgress).length < 1">
      <span class="error-message">No Todo task!</span>
    </p>
    <ul class="tasks">
      <li v-for="task in switchTasks" :key="task.id">
        <input
          type="checkbox"
          v-bind:checked="selected ? task.completed : !task.completed"
          @change="$emit('complete:task',task.id)"
        />
        <span :class="{'task-item-completed': task.completed}">{{ task.task }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ListItem",

  data() {
    return {
      selected: true,
      taskCompleted: false
    };
  },

  props: {
    tasks: Array
  },

  computed: {
    switchTasks() {
      if (this.taskCompleted) {
        return this.tasks.filter(this.inProgress);
      } else {
        return this.tasks;
      }
    }
  },

  methods: {
    inProgress(task) {
      return !this.isCompleted(task);
    },
    isCompleted(task) {
      return task.completed;
    }
  }
};
</script>