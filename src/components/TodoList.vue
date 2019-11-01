<template>
  <div class="content">
    <div class="sub-content">
      <div class="sub-content-element">
        <span>
          <input
            type="text"
            class="search-form"
            id="filter"
            v-model="filterTask"
            @keyup.enter="FilterTask"
            placeholder="Search for TODO..."
          />
        </span>
      </div>

      <add-task-form @add:task="AddTask" />

      <p>
        <list-item :tasks="tasks" @complete:task="completeTask" @delete:tasks="clearAll" />
      </p>
    </div>
  </div>
</template>

<script>
import ListItem from "./ListItem.vue";
import AddTaskForm from "./AddTaskForm.vue";

export default {
  name: "TodoList",

  components: {
    ListItem,
    AddTaskForm
  },

  props: {},

  data() {
    return {
      filterTask: "",

      tasks: [
        {
          id: 1,
          task: "Create a Todo list with vue",
          completed: true
        },
        {
          id: 2,
          task: "Create a Todo list with Vanilla JavaScript",
          completed: true
        },
        {
          id: 3,
          task: "Create a Todo list with react",
          completed: false
        },
        {
          id: 4,
          task: "Create a Todo list with angular",
          completed: false
        }
      ]
    };
  },

  methods: {
    FilterTask() {
      this.$emit("filter:task", this.filterTask);
      alert("Searching isn't functional yet!..");
    },
    AddTask(todoTask) {
      const lastId =
        this.tasks.length > 0 ? this.tasks[this.tasks.length - 1].id : 0;
      const id = lastId + 1;
      const completed = false;
      const newTodoTask = { ...todoTask, id, completed };

      this.tasks = [...this.tasks, newTodoTask];
    },
    completeTask(id) {
      const targetId = id - 1;
      this.tasks[targetId].completed = !this.tasks[targetId].completed;
    },
    clearAll() {
      this.tasks = [];
    }
  }
};
</script>
