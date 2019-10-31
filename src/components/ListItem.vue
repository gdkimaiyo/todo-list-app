<template>
  <div class="sub-content-element">
    <h4>TODO</h4>
    <div v-if="tasks.length < 1">
      <span class="error-message">No available tasks</span>
    </div>
    <div v-else>
      <p>
        <!-- <button class="btn-danger" @click="$emit('remove:task')">Remove Completed</button> -->
      </p>
      <ul class="tasks">
        <li v-for="task in tasks" :key="task.id">
          <button class="btn-danger" @click="$emit('delete:task',task.id)">
            <i class="material-icons">delete</i>
          </button>
          <input
            type="checkbox"
            v-bind:checked="selected ? task.completed : !task.completed"
            @change="$emit('complete:task',task.id)"
          />
          <span :class="{'task-item-completed': task.completed}">{{ task.task }}</span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "ListItem",

  data() {
    return {
      selected: true
    };
  },

  props: {
    tasks: Array
  },

  computed: {},

  methods: {}
};
</script>