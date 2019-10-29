<template>
  <div class="sub-content-element">
    <h4>TODO</h4>
    <p>
      <button class="btn-danger" @click="removeTask">Remove Completed</button>
    </p>
    <ul class="tasks">
      <li v-for="task in tasks" :key="task.id">
        <button class="btn-done" @click="completeTask">Done</button>
        <span>{{ task.task }}</span>
      </li>
    </ul>
  </div>
</template>

<script>
// import BaseButton from "./BaseButton.vue";

export default {
  name: "ListItem",

  props: {
    tasks: Array
  },

  computed: {},

  methods: {
    completeTask(ev) {
      ev.preventDefault();
      alert("completeTask isn't functional yet!..");
    },
    removeTask(ev) {
      ev.preventDefault();
      alert("removeTask isn't functional yet!..");
    }
  }
};
</script>